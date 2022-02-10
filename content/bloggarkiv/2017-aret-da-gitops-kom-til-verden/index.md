---
# Publishing mode
# draft = false means content is published. 
draft: false
# end

title: "2017, året GitOps kom til verden"

ingress: GitOps er eit rammeverk ein kan bruke i Continous Delivery, og blei nevnt for første gang i 2017 av Weaveworks. Same år fekk Digdir eigne erfaringar med lignande tankegang under etableringa av eInnsyn.
image: /gitops-weave-works.png
image_alt: "illustration"

# Meta
date: 2022-02-10T08:10:17+01:00
readtime: 5 minutter
---

På vårparten i 2017 var ein av Digdir sine løysingar [einnsyn.no](https://einnsyn.no/) under etablering og ein såg på måtar å overlevere applikasjonar som skulle settast opp av drift. Grunna retningslinjer for tilgangstyring kunne ein ikkje la utvikling få direkte tilgang til containerplattformen for å rulle ut applikasjonar. Ein måtte finne ei løysing som kunne gi utvikling tilgang til å sette i gang utrulling inndirekte. eInnsyn er ei løysing basert på mikrotjeneste, og blei levert via Docker Compose filer.

Med all applikasjonskonfigurasjon i tekstformat via Docker Compose blei det naturleg å plassere det i versjonskontroll via produktet [GitLab](https://about.gitlab.com/), som er basert på [Git](https://git-scm.com/). Her kunne utvikling og drift ha ein sentral versjon av konfigurasjonen, og drift kunne styre tilgang inndirekte til containerplattform via å gi rettigheiter i GitLab. Hadde ein utviklar eller systembrukar eigd av utvikling rettigheiter til å oppdatere konfigurasjon i GitLab, so reflekterte det rettigheiter for å rulle ut ein applikasjon. Ein kunne og reflektere miljø som som «test» via ein branch «test» og styre rettigheiter på branchen som igjen styrte kva rettigheiter ein hadde mot miljø «test».

Vidare såg ein fleire fordelar der endringar på løysingen blei naturleg spora via Git sin håndtering av versjonering, synleg for både utvikling og drift, og det kunne integrerast i ein [CI/CD](https://en.wikipedia.org/wiki/CI/CD) pipeline som både utvikling og drift hadde eigarskap til.

I august 2017 la [Weaveworks](https://www.weave.works/) ut eit blogginnlegg, [​GitOps - Operations by Pull Request](https://www.weave.works/blog/gitops-operations-by-pull-request), der dei lanserte begrepet «GitOps». Weaveworks oppsummerte då GitOps slik (fritt oversatt):
> *	Deklarativ konfigurasjon
> *	Endringar blir starta via pull request / merge request
> *	Sentral plass for konfigurasjon og «sannheiten» om systemet
> *	Verktøy for å håndtere synkronisering og avdekke forskjellar mellom konfigurasjon og system
> *	Tilbakerulling og auditloggar via Git 

Weaveworks fekk her etablert eit uttrykk, som 5 år etter lev i beste velgåande. GitHub og GitLab blir stadig utvida med meir relevant funksjonalitet, som for eksempel GitHub Actions. Andre produkt blir også utvikla for å støtte oppunder denne tankegangen, som for eksempel ArgoCD for å synkronisere «sannheiten» og ønska tilstand for konfigurasjon til Kubernetes. RedHat leverar blant anna ein GitOps Operator til OpenShift, og har eiga underside for GitOps for kva dei legg i det, [What is GitOps?](https://www.redhat.com/en/topics/devops/what-is-gitops). Ellers har dei store skyleverandørane også eksempel på bruk av GitOps i sine produkt:
*	[GitOps for Azure Kubernetes Service](https://docs.microsoft.com/en-us/azure/architecture/example-scenario/gitops-aks/gitops-blueprint-aks)
*	[GitOps-style continuous delivery with Cloud Build](https://cloud.google.com/kubernetes-engine/docs/tutorials/gitops-cloud-build)
*	[Building a GitOps pipeline with Amazon EKS](https://aws.amazon.com/blogs/containers/building-a-gitops-pipeline-with-amazon-eks/)


GitOps sett i sammenheng med DevOps gir ei veldig god samarbeidsflate, sentral kilde for konfigurasjon for utvikling og drift, og fleksibilitet der autonome team kan ha sine eigne repository som blir kobla opp til gitt miljø applikasjonane køyrer i. 

I eit etableringsprosjekt me jobbar med no har me teke i bruk GitHub som Git komponent og kombinert det med [ArgoCD](https://argo-cd.readthedocs.io/en/stable/) som står for å synkronisere konfigurasjon mellom GitHub og Kubernetes.

Avsluttar her med ein link til Weaveworks sin  [Guide To GitOps](https://www.weave.works/technologies/gitops/)


	



