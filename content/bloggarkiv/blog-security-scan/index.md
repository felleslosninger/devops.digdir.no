---
# Publishing mode
# draft = false means content is published.
draft: false
# end

title: "Shift-left-security: Sårbarheitsscanning i praksis"

ingress: "I ei verd der sårbarheiter blir raskt utnytta er sårbarheitscanning av Docker containere eit nyttig verktøy for å unngå at applikasjonane våre har kjente sårbarheiter. Her ser me på nokre mogeleg verktøy blant mange for å gjere dette."
image: /scan-for-bugs.jpg
image_alt: "Scan for bugs in code"

# meta
meta: true
date: 2022-04-27T13:45:36+02:00
readtime: 10 minutter
author: Randi Øyri
---

I dag leverer dei fleste utviklarar docker images av koden sin uavhengig av programmeringsspråk. Det er stort sett slutt på tida då ein java-utviklar leverte ei svær EAR eller WAR fil eller på andre sære format.  Så denne standardiseringa gjer at koden kan køyrast enklare opp og meir likt f.eks. i eit Kubernetes-miljø. Det betyr også at ein kan bruke dei same verktøya for deploy og ulike typar testar, og ikkje minst for for å unngå sårbarheiter. Dette vil me påstå gir oss ei betre verktøykasse å velgje frå.

Sikkerheit dekkar mykje, så det kan vera vanskeleg å prioritere og ikkje minst rekke over. Her kan Sysdig sin rapport ["2022 Cloud-Native Security And Usage Report"](https://sysdig.com/resources/reports/s-2022-cloud-native-security-and-usage-report/) hjelpe oss å prioritere.  Sysdig har undersøkt over 3 millionar containers som anten kundane deiras køyrer eller ligg ope på Github, Docker Hub eller CNCF.

{{< image src="./sysdig-key-trends-2021.jpg" >}}
Her ser me tydeleg at i eit container-basert miljø, så har 75% av containerne "high" eller "critical" sårbarheiter.
{{< /image >}}

Den høge andelen alvorlege sårbarheiter funne i containere i bilde over tyder på at me bør ha fokuse på sårbarheitsscanning. Så kva verktøy kan hjelpe oss?

Men fyrst kort om oss. Me jobbar i dag med å etablere ny systemarkitektur for ID-porten med venner, deriblant ny byggepipeline på Github med Github actions. I den gamle arkitekturen gjorde me alt sjølve med å bygge opp komplette byggepipeline med Jenkins (configuration-as-code) internt. Dette gav oss store fordelar mtp fart, men var også veldig krevjande å vedlikeholde og tungt å oppdatere til nye versjonar av skogen av jenkins plugins. Difor ser me i dag på i større grad å kjøpe dette som ei teneste som let oss fokuser å kjerneapplikasjonane og beholde farten. Der passar Github actions godt inn. Her plukkar me ut actions (slags plugins) me ynskjer og lagar bibliotek med workflow-filer som me kan gjenbruke på tvers av Github repositories. Då finst det også actions som pakkar inn container-scanning tenester som Trivy. [Trivy](https://aquasecurity.github.io/trivy) er ei verdsleiande open-source teneste for sårbarheitscanning i byggepipeline i dag. Målsettinga deira er at den skal vera enkel å bruka i CI/CD og er difor eit godt val for oss.

I dag brukar me Azure/container-scan actions som nyttar Trivy og Dockle. Dockle er container linter som hjelper til med å best practies for å bygge opp docker image og CIS Benchmark. Trivy har også eigen Github action, men denne har me ikkje testa ut. Les meir om desse [her](https://aquasecurity.github.io/trivy/v0.19.1/advanced/integrations/github-actions/).

{{< image src="./container-scan-log4shell.jpg" >}}
Me har erfart at container-scan har stoppa log4shell og mange andre sårbarheiter, så dette har gitt oss eit betre sikkerheitsnett, som sårbarheiten oppdaga av Trivy/Container-scan her.
{{< /image >}}

## "Container-scan stoppar meg frå å kode"
Men blir ikkje dette berre meir jobb for utviklarane? Endå ein ting som skal «left»? Vel, det kostar ganske mykje å fikse sårbarheiter i produksjon også og trur at dei som eig produktet set pris på sikkerheitsnettet som sårbarheitscanning gir oss.

Så nokre små tips til deg frå oss:
Bruk minst mogeleg docker image som base-image, helst distroless med minimalt med os-pakkar. Dess mindre kode, dess mindre potensial for sårbarheiter.
Tilsvaranade i applikasjonen din, treng du eigentleg å ta ein dette 3.-parts biblioteket? Gir det nok verdi? Kan du skrive det same sjølv?

Hugs å oppdater base docker image.
Velg gjerne noko som oppdaterer min. minor versjonar automatisk, som automatisk bygging av docker images via f.eks. Maven plugins:
* Spring-boot build-image (bruker Packito build tools)
* Google Jib
Desse lagar docker images etter best-practices og oppdaterer base-versjonar, me lever i ein Spring boot verden og har gode erfaringar med å køyre spring boot sin versjon med minimal distro slik:

{{< code >}}
mvn -B spring-boot:build-image --file pom.xml -Dspring-boot.build-image.imageName=myRegistry/myimage:v1 -Dspring-boot.build-image.builder=paketobuildpacks/builder:tiny
{{< /code >}}

Om du bygger opp docker image sjølv, så ikkje set minor versjon på base-image, men vel major versjon for å få automatisk med neste minor versjon ved bygging. F.eks. for Tomcat eller/og java versjoner. Det krev meir å bygge opp imaget sjøl, du må sjøl passe på å følgje best practices som f.eks. aldri køyr som root. Det gjorde 76% av container i undersøkelsen til Sysdig. Les om best practies f.eks. hos [Docker](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)

Og dersom sårbarheiten stoppar bygget ditt, men du har undersøkt og den er ikkje relevant for din applikasjon? Legg den inn i allowed-list for tillatte unntak. Men ver nøye med å vedlikeholde denne lista og fjerne unntaka etter kvart som bibliotek/os blir patcha.

## Produksjon?
Å sjekke ny eller endra koda i pipeline er jo fint og flott, men kva med det som er i produksjon? Det er jo produksjon som er viktigast! I produksjon bør ein sjå kva verktøy container-plattforma kan tilby. Azure Portal har sitt [Security Center/Defender for Cloud](https://azure.microsoft.com/nb-no/services/defender-for-cloud/#features). Dette gir varsel og prioriterer sårbarheiter for deg. Tilsvarande har Redhat Openshift enterprise "Advanced Cluster Security for Kubernetes" som også gir veldig bra overblikk der ein kan drille ned på applikaskjonane/pod-ane. Andre plattformer har sikkert tilsvarande løysingar.

Sysdig rapporten er også tydleg på at ein bør sjekke både i pipeline og i produksjon:
"… all containers are continuously rescanned post deployment to discover any newly disclosed vulnerabilities, but scanning as much as possible pre deployment will prevent known flaws from appearing in production at all."

## Dependency scan
Eit anna verktøy som er veldig nyttig for å unngå sårbarheiter er [Github dependabot](https://github.blog/2020-06-01-keep-all-your-packages-up-to-date-with-dependabot/) (o.l. verktøy) som oppdatere bibliotek ved å automatisk opprette Pull Requests. Dette kan konfigurerast til å godkjennast automatisk også om det er non-breaking changes/grønne testar. Ofte ynskjer ein å vera litt restriktiv og undersøkje sjølv også (sjå over endringane i changeloggen). Dette gjera at ein enklare får med seg alle oppdateringar og dermed også sikkerheitspatchar i bibliotekt. Dette kan også konfigurerast til å brukast for dine private repositories.


Dette var kort om tenester/verktøy me nyttar i skya for å hjelpe oss med å levere kode utan kjente sårbarheiter. Det er nok også mykje anna å velgje i der ute, berre pass på å ta i bruk dei gode verktøya og tenestene som ligg enkelt tilgjengeleg!

## Kjelder
{{< footnote >}}
Rapport sysdig: https://sysdig.com/resources/reports/s-2022-cloud-native-security-and-usage-report/
Github Actions: https://github.com/features/actions
Trivy: https://aquasecurity.github.io/trivy
Azure container-scan: https://github.com/Azure/container-scan
Trivy github actions: https://github.com/aquasecurity/trivy
Docker best practices: https://docs.docker.com/develop/develop-images/dockerfile_best-practices/
Spring boot maven plugin for build-image: https://docs.spring.io/spring-boot/docs/current/maven-plugin/reference/htmlsingle/#goals-build-image
Google Jib: https://github.com/GoogleContainerTools/jib
Azure Portal security center: https://azure.microsoft.com/nb-no/services/defender-for-cloud/#features
RedHat Openshift Advanced cluster security for Kubernetes (ACS): https://cloud.redhat.com/products/kubernetes-security
Github dependabot: https://github.blog/2020-06-01-keep-all-your-packages-up-to-date-with-dependabot/
{{< /footnote>}}
