---
# Publishing mode
# draft = false means content is published. 
draft: false
# end

title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
ingress: Ingress (kort beskrivelse)
image: /illustrations/illustration_12.png
location: "Leikanger"
topics: "DevOps, Dev"
contact: "Ola Nordmann, test@domain.com"

# Registration URL
registration: "#"

---

# Program
Oversikt over program

### Mandag 08. Jan

| Emne   | Tidspunkt   | Sted        | Ansvarlig    | Kontakt        |
|-------------|--------|-------------|--------------|----------------|
| DevOps for dummies | 08:00-12:00 | Møterom 068 | Dag Dagens   | test@domain.no |
| Dev eller Ops? | 08:00-12:00    | Møterom 067 | Ola Nordmann | test@domain.no |
