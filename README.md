# Devopsdagar
Informasjonsside for Digdir Devopsdagar

https://devops.digdir.no

Nettsiden er tilgjengelig via github-pages:   
https://bookish-umbrella-3e531b6d.pages.github.io/ 

## Get started
1. Hugo installation: `https://gohugo.io/getting-started/installing/`
2. In project folder. Run application: `hugo serve -F`
3. Application available at: `localhost:1313`

## Create content
News: `hugo new nyhetsarkiv/my-post-title/index.md`

Arrangement: `hugo new arrangementarkiv/my-post-title/index.md`

### Configuration
- For completed arrangements, set `draft: true` in `arrangementsarchive/<title>/_index.md` to hide arrangement from published site.
- For future arrangements, alter `date` value in `_index.md`. Remember to run server with `-F` flag for future arrangement to be built.











