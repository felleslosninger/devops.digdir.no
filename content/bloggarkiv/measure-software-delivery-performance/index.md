---
# Publishing mode
# draft = false means content is published. 
draft: false
# end

title: "Systematisk måling av leveransekvaliteten til et DevOps team"

ingress: Hvordan vet vi om vi blir bedre på å levere programvare til produksjon? Burde vi starte å måle oss selv? Ikke for å sammenligne team mot team, men for å sammenligne mot vårt eget team for å lære og se om det vi gjør virker.
image: /four-metrics-dashboard.png

# Meta
date: 2022-01-20T19:00:01+01:00
readtime: 10 minutter
---
I sine [State of DevOps rapporter](https://www.devops-research.com/research.html#reports) benytter DORA fire metrikker for å måle leveransekapasiteten til et team hvorav to måler gjennomstrømningshastighet av endringer og to måler stabilitet på disse endringene. Utgangspunktet er at jo raskere du kan levere til produksjon, jo raskere kan du levere verdi til kundene. Det er verdt å merke seg at raskt ikke betyr å kompromisse på kvalitet - snarere tvert om. 

## Gjennomstrømningshastighet
### Ledetid for kodeendringer | Lead time for changes
Hvor lang tid går det fra en kodeendring er gjort til den er i produksjon? Her er det altså ikke snakk om hvor lang tid det tar å kode en endring, men hvor lang tid det går fra en utvikler sier seg ferdig til koden er ute i produksjon. Her liger de beste på under en time.

### Frekvens for produksjonssetting | Deployment frequency
Hvor ofte sender du kode for en gitt tjeneste/applikasjon til produksjon? Her ligger de beste på flere ganger om dagen som i praksis ofte betyr at så fort en endring er godkjent så går den automatisk ut i produksjon uten at det gir nedetid eller påvirker brukerne. 

## Stabilitet
### Tid til å gjenopprette en tjeneste | Time to restore service
Hvor lang tid tar det å gjennopprette en tjenste etter bortfall av tjenesten f. eks. hvis en server krasjer? Også her ligger de beste på under en time.

### Feilrate for endringer | Change failure rate
Hvor mange feil introduseres som følge av en produksjonssetting som påvirker brukerne negativt og som typisk fører til en feilretting (hotfix, rollback, patch)? Her ligger de beste på 0%-15%.

Dette er fire metrikker som er enkle å forholde seg til og som er relativt greie å måle - og sammen gir de oss et godt bilde på leveransekapasiteten til et team. Det kan være fristende å benytte slike metrikker til å sammenligne team, men det er en dårlig idé. Utgangspunktet til teamene og de tjenstene de har ansvar for vil være vidt forskjellig. Det som derimot gir mening er å benytte disse metrikkene til å måle mot seg selv. Man identifiserer startpunktet og hvor man ønsker å være. Deretter prøver man ut ulike tiltak, mange er godt beskrevet i State of DevOps rapportene, og måler effekten av disse.

DevOps handler om kontinuerlig læring og utvikling, både på individuelt nivå og på team nivå, men vi må vite om det vi gjør virker.

> For nerdene blant oss så har DORA har laget en løsning på åpen kildekode for automatisk innsamling av metrikkene med tilhørende dashboard. Koden ligger på [GitHub](https://github.com/GoogleCloudPlatform/fourkeys).
> 
> Her finner du også en [YouTube video](https://www.youtube.com/watch?v=2rzvIL29Nz0) som går i detalj på de 4 metrikkene