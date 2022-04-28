---
# Publishing mode
# draft = false means content is published. 
draft: false
# end

title: "Refaktorering - ei god investering"

ingress: Kode refaktorering er ein prosess nytta for å endre og rydde i eksisterande kode utan å endre korleis koden fungerer
image: /refaktorering/jenga.png
image_alt: "jenga"

# Meta
date: 2022-03-31T11:46:14+02:00
readtime: 10 minutter
---

Hugsar du første gong du løyste ei utfordrande kodeoppgåve? Eller om du ikkje har koda før så hugsar du kanskje ein gong du jobba med ei oppgåve som var litt for vanskeleg, eller bygde eit stort jenga tårn med mange brikkar utan at det datt ned. Då har du kanskje kjent på ei blanding av angst, frustrasjon, lettelse, glede medan du arbeidde med det, løyste det og fekk det til å fungere akkurat som det skulle. Så kjem tilbakemeldingane og du må gjere endringar for å utbetre det du laga. Då har du kanskje kjent på frykta ved tanken på å gjere endringar på denne flotte velfungerande tingen du har laga og tenkjer kanskje: *"om eg endrar på noko no så sluttar det kanskje å fungere, kanskje eg gjer ein feil og då klarer eg ikkje å fikse den igjen."* Slik tenker du gjerne første gong når du skal refaktorere kode du ikkje heilt forstår sjølv om du nettopp skreiv den. Då kjem gjerne kjenslene av angst og frustrasjon tilbake for å prøve å hindre deg frå å lykkast. Om du let desse kjenslene være kjensler, og prøver så vil du kanskje sjå at du klarer det og koden blir enklare å lese, ryddigare og enklere å gjenbruke. Enkel, elegant og gjenbrukbar kode, det er ei herleg kjensle det.

> *Kode-refaktorering er ein prosess nytta for å endre og rydde i eksisterande kode utan å endre korleis koden fungerer*

Poenget med å refaktorere er å gjere koden meir effektiv og vedlikehaldbar. Å investere litt i refaktorering i dag kan spare deg for mykje teknisk gjeld i framtida. Det er mykje betre å rydde i koden med ein gong enn å ta jobben seinare når kodebasen har blitt endå større. Enkel og vedlikehaldbar kode kostar mindre tid og krefter å sette seg inn i, eller endre i framtida. 

For å unngå at koden råtnar, er refaktorering essensielt. Duplikat kode, dårlege klassifiseringar, hastearbeid og andre avvik frå "best practices" kan føre til at kodebasen råtnar. "Jo Fleire kokkar jo meir søl" er eit kjent begrep som kan passe her. Om ein ikkje ryddar etter seg på kjøkkenet så blir det mindre plass og vanskelegare neste gong ein skal lage mat. Det samme gjeld kodebasen. Difor er det viktig å rydde etter seg. Konsekvent navngjeving er eit godt hjelpemiddel for god kodekvalitet.

## Kva har dette med DevOps å gjere?

Ein bør ta seg tid til å refaktorere før ein legg til nye features, eller nye oppdateringar til eksisterande kode. Eller kanskje ein nettopp har produksjonssett ein ny stor flott feature, så er gjerne dette eit av dei beste tidspunkta å rydde litt før ein seie seg ferdig. I DevOps, eller smidig utvikling generelt, er det å rydde i tidlegare skrevet kode heilt essensielt for å kunne halde flyten og utviklingstakten oppe.

Extreme programming (XP) er ein utviklingsmetodikk der smidig utvikling er heilt sentralt saman med testing og refaktorering. I XP så er dette faktisk så viktig at ein skriv testane først, før ein skriv kode. Dette er kjent som Test Driven Development (TDD), og det bidreg til høg testdekning av kodebasen. TDD fungerer slik at først skriv du ein test som feilar (raud), og så skriv du nok kode til at testen passerer (grøn), før du refaktorerer for å optimalisere og rydde i koden utan at du endrar på korleis den fungerer. 

![refaktorering rød grøn metode](/refaktorering/tdd.png)

> *Tips: Refaktorer før du legger inn nye features*

## Korleis kan det gjerast?

Start enkelt med eit steg om gongen, fulgt opp av testing. Bryt ein arbeidet ned i mindre delar så er det meir overkommelig og enklare å teste. Nokon gongar treng ein meir domenekunnskap og utforske mulighetane for å finne enklare løysingar. Under ser du eit døme der eit tidspunkt skal settast på eit gitt format:


``` java
        <...>
        LocalDateTime saDato = LocalDateTime.parse(mt.getNoarksak().getSaDato());
        XMLGregorianCalendarImpl xmlGregorianCalendar = new XMLGregorianCalendarImpl();
        xmlGregorianCalendar.setYear(saDato.getYear());
        xmlGregorianCalendar.setMonth(saDato.getMonthValue());
        xmlGregorianCalendar.setDay(saDato.getDayOfWeek().getValue());
        xmlGregorianCalendar.setHour(saDato.getHour());
        xmlGregorianCalendar.setMinute(saDato.getMinute());
        xmlGregorianCalendar.setSecond(saDato.getSecond());

        arkivmelding.setTidspunkt(xmlGregorianCalendar);
        return arkivmelding;
```

Koden opprettar ein *saDato* som held på ein gitt dato og tidspunkt, før den vert putta inn i eit XMLGregorianCalendarImpl objekt som held på dato og tidsinformasjon. Dette objektet vert så satt som tidspunkt i *arkivmelding* og denne vert returnert. 
I dette dømet så er det mulig å refaktorere, forenkle og finne smartare måtar å gjere ting på. Vha hjelpemetodar tilgjengelig i denne applikasjonen så kan ein parse *saDato* direkte til rett format og sette tidspunktet.

``` java
        <...>
        arkivmelding.setTidspunkt(DateTimeUtil.toXMLGregorianCalendar(mt.getNoarksak().getSaDato()));
        return arkivmelding;
```

> *Tips: Test ofte*

## Konklusjon

Tenk på kode refaktorering som eit reint og ryddig kjøkken. Det er enkelt å finne fram og enkelt å lage mat. Du slepp å rydde før du skal lage middagen og tida spart kan du bruke til noko kjekt! 

Ikkje være redd for å gjere endringar i koden, refaktorering vil auke din eiga forståing og gjere deg endå flinkare til neste gong. 

Kode refaktorering er ein viktig praksis for å tilrettelegge slik at DevOps og smidig utvikling skal fungere optimalt. Ein ryddig kodebase gjer det enklare å forstå og enklare å lage nye features. Refaktorering er ei nedbetaling av teknisk gjeld, og dette er lurt å gjere før rentene samlar seg opp. 

--- 

Avslutningsvis ynskjer vi å dele nokre sitat frå Martin Fowler.


> *“I’ve found that refactoring helps me write fast software. It slows the software in the short term while I’m refactoring, but it makes the software easier to tune during optimization. I end up well ahead.”*
>
> Martin Fowler, Refactoring: Improving the Design of Existing Code

> *"“Whenever I have to think to understand what the code is doing, I ask myself if I can refactor the code to make that understanding more immediately apparent.”"*
>
> Martin Fowler, Refactoring: Improving the Design of Existing Code

> *“When you find you have to add a feature to a program, and the program's code is not structured in a convenient way to add the feature, first refactor the program to make it easy to add the feature, then add the feature.”*
>
> Martin Fowler, Refactoring: Improving the Design of Existing Code
