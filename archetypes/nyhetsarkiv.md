---
# Publishing mode
# draft = false means content is published. 
draft: false
# end

title: "{{ replace .Name "-" " " | title }}"
ingress: Ingress (kort beskrivelse)

meta: true
date: {{ .Date }}
---