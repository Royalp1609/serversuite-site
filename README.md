# Server Suite website

Website and documentation for [Server Suite for Pterodactyl](https://github.com/royalp1609/serversuite-pterodactyl),
built with MkDocs Material and published to GitHub Pages:
https://royalp1609.github.io/serversuite-site/

Every push to `main` builds the site (`mkdocs build --strict`) and deploys it
(`.github/workflows/pages.yml`). Pull requests build it without deploying.

Preview locally:

    docker run --rm -it -p 8000:8000 -v "$PWD":/docs squidfunk/mkdocs-material:9.6.14 serve -a 0.0.0.0:8000
    docker run --rm -v "$PWD":/docs squidfunk/mkdocs-material:9.6.14 build --strict

Screenshots: `docs/assets/screenshots/pterodactyl/`, 1440x900, dark theme, taken on demo
servers with internal addresses masked. `listings/` holds the copy for marketplace listings.

Licence: AGPL-3.0, like Server Suite itself.
