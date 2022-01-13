---
# Publishing mode
# draft = false means content is published. 
draft: false
# end

title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
ingress: Ingress (kort beskrivelse)
---