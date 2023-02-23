---
# Publishing mode
# draft = false means content is published. 
draft: false
# done = true means arrangemnt is completed and archived
done: false
# end

# Content
title: "{{ replace .Name "-" " " | title }}"
ingress: Ingress (kort beskrivelse)
image: /illustrations/devops.png
image_alt: "illustration"

# Meta
start_date: "7. Mars 2023"
location: "Leikanger"
topics: "DevOps, Dev"
contact: "Ola Nordmann, test@domain.com"
deadline: "påmeldingsfrist 01.01.01"

# Action buttons
actions:
    - title: Påmelding
      url: "#"
      disabled: true
      disabled_message: "Påmelding er avsluttet"
    - title: Vil du holde presentasjon?
      url: "#"
      disabled: false

---

# Program
Oversikt over program

### Mandag 08. Jan

| Emne   | Tidspunkt   | Sted        | Ansvarlig    | Kontakt        |
|-------------|--------|-------------|--------------|----------------|
| DevOps for dummies | 08:00-12:00 | Møterom 068 | Dag Dagens   | test@domain.no |
| Dev eller Ops? | 08:00-12:00    | Møterom 067 | Ola Nordmann | test@domain.no |
