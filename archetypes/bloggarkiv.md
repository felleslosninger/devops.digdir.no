---
# Publishing mode
# draft = false means content is published. 
draft: false
# end

title: "{{ replace .Name "-" " " | title }}"

ingress: Ingress (kort beskrivelse)
image: /illustrations/illustration_12.png
image_alt: "illustration"

# Meta
date: {{ .Date }}
readtime: 10 minutter

author-id: "<author-id>"
---