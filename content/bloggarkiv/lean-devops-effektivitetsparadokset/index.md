---
# Publishing mode
# draft = false means content is published. 
draft: false
# end

title: "Lean og effektivitetsparadokset"
date: 2022-03-02T20:00:00+01:00
ingress: På konseptnivå er ofte DevOps definert ved CALMS. Det er ei forkorting for Culture, Automation, Lean, Measuring og Sharing. Lean har mange betydninger og tolkninger, eg vil trekke fram eit par element som er godt skildra i boka “This is Lean” av Niklas Modig og Per Ahlstrøm. Er det fleire måter å måle effektivitet på? Og kva er effektivitetsparadokset?

image: /lean-devops-effektivitetsparadokset.png
image_alt: "illustration"

# meta
meta: true
readtime: 5 minutter
---
Lean har sin opprinnelse frå Toyota og deiras måte å organisere sin produksjon på. Noko av det som går igjen når ein snakker om Lean er at ein skal minimere unødvendig bruk av ressurser som ikkje tilfører verdi for sluttkunden eller til sluttproduktet.

Lean beskriver to perspektiver på effektivitet. Den eine er ressurseffektivitet der ein har fokus på at alle ressurser i ein organisasjon er godt utnytta. Dette betyr at alle tilsette alltid har fullt opp med oppgåver(og i tillegg ofte oppgåver ventende i kø). Dei er 100% effektive for dei har alltid noko å jobbe med. Mange organisasjoner er fokuserte på nettopp denne måten å måle effektivitet på, det kan til og med være målet i seg sjølv for organisasjonen å ha høg utnyttelse av ressursene.

Frå eit anna perspektiv kan ein sjå for seg eit produktet, eller for ei utviklingsavdeling ein program-feature, som de ansatte jobber på. Ved å følge denne featuren frå behovet oppstod hjå kunde og til den nye featuren er ferdig levert og gir verdi til sluttkunde, har ein flytta fokuset frå ressurs-bruk til feature-flyt. Ein prioriterer å få tiden frå behovet oppstod til feature er levert så lav som mulig. For å oppnå dette tilstreber ein å tilføre mykje ressurser over kort tid. Denne måten å måle effektivitet på kalles flyteffektivitet. Her er det einheiten, eller i dette tilfellet ein feature, som skal flyte raskest mulig gjennom verdistrømmen i ein organisasjon.

![alt text](/lean-devops-effektivitetsparadokset.png "Dino comics - effektivitet")

Ein kan fort tenke at ved å tilføre samme mengde arbeid til ein ny feature så vil det være like effektivt å ha fokus på ressurseffektivitet som flyteffektivitet. Her argumenterer Lean for at ved å overfokusere på ressurseffektivitet vil flyteffektiviteten bli lågare. Når flyteffektiviteten blir lågare vil kvar feature bruke lengre tid gjennom verdikjeden, ein vil ha fleire features i prosess samtidig og ein vil typisk måtte plukke opp featuren fleire ganger for å jobbe med den i ulike steg. Denne måten å organisere arbeidet på fører med seg ein del negative konsekvenser. Desse er lette å kjenne seg igjen i som t.d kostnaden ved context-switching, ein mister forståelse og leverer lavere kvalitet, det oppstår møtekollisjoner fordi ressurser er opptatt og mange overleveringer fører til fleire feil og misforståelser. Dette igjen vil føre til generering av sekundærbehov for å få løyst primæroppgåvene som er påkrevd for å få featuren ferdig. Desse sekundærbehovene tilfører ikkje direkte verdi til sluttproduktet og blir kategorisert som overflødig arbeid.

Effektivitetsparadokset kan forklares med dette overflødige arbeidet. Når ein overfokuserer på ressurseffektivitet vil det gå ut over flyteffektiviteten(featurer køes opp i flaskehalser). Dette vil igjen føre til at det oppstår sekundærbehov. Aktivitetene for å dekke desse sekundærbehovene kan oppfattes som verdifulle aktiviteter, men desse aktivitetene er overflødige viss primærbehovet allerede er dekka. Altså unødvendig arbeid. Paradokset er at me tilsynelatende utnytter ressursene våre godt, men i realiteten er me ineffektive, sidan mykje av arbeidet som blir gjort er overflødig og ikkje verdiskapende.

Lean setter flyteffektivitet framfor ressurseffektivitet. Det er ein strategi som setter kunden og deira behov i fokus og organisasjonen bygges opp for å understøtte dette. Det er ikkje nødvendigvis fokus på at alle ansatte skal utnyttes 100%, men heller at de i fellesskap, raskt og med god kvalitet leverer verdi for sluttkunden. I DevOps er Lean eit sett med prinsipp for å eliminere unødvendig arbeid og optimalisere flyt av ny funksjonalitet til produksjon.

Er du nysgjerrig på korleis ein går fram for å løyse effektivitetsparadokset i ein organisasjon? Då anbefaler eg boka “This is Lean”.

![alt text](/this_is_lean.png "This is Lean")