# Devopsdagar
Informasjonsside for Digdir Devopsdagar:  
https://devops.digdir.no

Nettsiden er laget med Hugo (static-site-generator). 

## Kom i gang
1. Sett opp Hugo: `https://gohugo.io/getting-started/installing/`
2. Start applikasjon. Gå til prosjekt og kjør `hugo serve -F`
3. Nettside tilgjengelig på: `localhost:1313`

## Opprette innhold
Innhold for nettsiden er skrevet i Markdown. Og det finnes 2 innholdstyper:
- Nyheter: `hugo new nyhetsarkiv/my-post-title/index.md`
- Arrangementer: `hugo new arrangementarkiv/my-post-title/index.md`
- Blogg: `hugo new bloggarkiv/my-blog-title/index.md`

### Konfigurasjon
- For fullførte arrangementer. Sett `draft: true` i `arrangementsarchive/<title>/_index.md` for å skjule på nettside. Dette gjelder også andre innholdstyper som ikke ønskes publisert
- For arrangementer frem i tid, endre `date` verdien i arrangementets `_index.md`. For at Hugo skal ta med fremtidige arrangement må server kjøres med `-F` parameteret. e.g `hugo serve -F`.











