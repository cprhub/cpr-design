# cpr-design

Undervisningsmateriale til Coding Pirates Rødovres Design-hold — bygget med
[MkDocs Material](https://squidfunk.github.io/mkdocs-material/) og udgivet
via GitHub Pages, samme opsætning som søsterprojektet
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
  index.md                          # forside
  assets/                           # CP-logo, favicon
  stylesheets/extra.css             # CP-farver + fonte (Bungee/Lato)
  autumn-2026/
    index.md                        # sæson-oversigt
    design-hold/
      index.md                      # 13-ugers oversigt
      week-01-pirat-logo/index.md   # ugeside (skabelon, se kommentar i filen)
```

Design følger [Coding Pirates Danmarks designguide](https://codingpirates.dk/designguide/)
(farver, Bungee/Lato-fonte, logoregler).
