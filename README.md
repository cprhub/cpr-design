# cpr-design

Undervisningsmateriale til Coding Pirates Rødovres hold (Juletog og Pinball)
— bygget med [MkDocs Material](https://squidfunk.github.io/mkdocs-material/)
og udgivet via GitHub Pages, samme opsætning som søsterprojektet
[cpr-microbit](https://itsgauravsaxena.github.io/cpr-microbit/).

## Kør siden lokalt

```bash
pip install -r requirements.txt
mkdocs serve
```

Åbn derefter http://127.0.0.1:8000 i browseren.

## Udgivelse

Siden bygges og udgives automatisk til GitHub Pages, hver gang der pushes
til `main` (se `.github/workflows/deploy.yml`). Slå GitHub Pages til under
**Settings → Pages → Deploy from branch → gh-pages**.

## Struktur

```
docs/
  index.md                          # forside, lister holdene
  assets/                           # CP-logo, favicon
  stylesheets/extra.css             # CP-farver + fonte (Bungee/Lato)
  juletog/
    index.md                        # 13-sessioners oversigt
    session-01-opsaetning/index.md  # sessionsside (skabelon, se kommentar i filen)
  pinball/
    index.md                        # sessionsoversigt (indhold mangler stadig)
    session-01/index.md … session-13/index.md   # sessionssider (tomme skabeloner)
```

Design følger [Coding Pirates Danmarks designguide](https://codingpirates.dk/designguide/)
(farver, Bungee/Lato-fonte, logoregler).
