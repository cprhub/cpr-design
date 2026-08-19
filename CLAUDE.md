# Coding Pirates Rødovre – Design-hold undervisningsmateriale

## Opgaven
Dette repo indeholder undervisningsmateriale til **Coding Pirates Rødovre's Design-hold** — et **13-ugers forløb**. Formålet med dette projekt er at hjælpe med at skrive, strukturere og vedligeholde det materiale, en frivillig underviser bruger direkte i undervisningen.

Reference/inspiration (anden holdleders materiale, samme forening): https://itsgauravsaxena.github.io/cpr-microbit/ — brug den til at forstå tone, opbygning og niveau, men indholdet her er en anden disciplin (3D-design, ikke micro:bit).

Sitet bygges med **MkDocs Material** og udgives via GitHub Pages (se `.github/workflows/deploy.yml`). Følg den eksisterende mappestruktur og front matter — se `README.md` for detaljer.

## Målgruppe (gælder for alt indhold)
- Børn på **10-12 år**.
- **Altid begynderniveau** — ingen forudsætninger antages, heller ikke fra tidligere uger, da nye pirater kan komme til undervejs. Byg kort genopfriskning ind, hvis en uge bygger på noget tidligere.
- Sprog: **dansk er kildesprog** (engelsk oversættelse findes via i18n-pluginnet, når den er lavet). Tone: legende, opmuntrende "sørøver"-stil som resten af Coding Pirates — kort, konkret, lidt humor. **Ingen emojis** (heller ikke i overskrifter/pitch) — brug ordvalg og "!" til at bære tonen i stedet. Undtagelsen er ✅ som fast statusikon i "✅ Færdig når..."-overskrifter og status-kolonner, det er struktur, ikke tone. Undgå at virke nedladende for 12-årige.

## Design-holdets indhold
Holdets efterår 2026-forløb er **ét sammenhængende 3D-design-projekt**, ikke en blanding af discipliner: piraterne designer og 3D-printer deres eget **LEGO-kompatible juletog** i **Tinkercad**, inspireret af det klassiske LEGO-juletog. Toget skal kunne køre på rigtige LEGO-skinner (sporvidde ca. 37,5 mm), så forløbet inkluderer også at måle, designe efter mål, og teste/justere print undervejs. Se den fulde ugeoversigt i `docs/autumn-2026/design-hold/index.md`.

- **Software:** Tinkercad (gratis) — se software-krav nedenfor.
- **Udstyr:** Egne bærbare (Windows/Mac) + **Bambu Lab A1 Mini** (holdets flerfarvede printer, bruges løbende, maks. 1 time pr. print) + **TekX-printere** (eksterne, én farve ad gangen, til store funktionelle dele — besøg i uge 7, 10 og 11).
- **Metode:** Hver del af toget designes som sin egen fil/objekt, så den kan printes/males i egen farve.

Fremtidige sæsoner/hold under dette repo kan sagtens dække andre design-discipliner (grafisk design, spildesign, web/UI) — men det er *ikke* efterår 2026-forløbet, og skal ikke blandes ind i den eksisterende ugeoversigt uden eksplicit aftale.

## Software-krav (ufravigeligt)
- Undervisning foregår på **Windows og Mac** — ingen løsninger der kræver iPad/Chromebook.
- **Kun gratis eller open source programmer.** Aldrig noget der kræver betalt licens/abonnement/"pro"-version for at gennemføre øvelsen.
  - Tinkercad er gratis at bruge til dette formål.
  - Hvis et værktøj har både gratis og betalt niveau: undersøg og bekræft, at gratis-niveauet er nok til øvelsen — ellers find et alternativ.
- Ved tvivl om pris eller platformsunderstøttelse: **slå det op**, gæt ikke.

## Uge-struktur (13 uger)
- Uge 1: en "quick win" — noget der virker med det samme og giver mestringsfølelse.
- Gradvist stigende sværhedsgrad hen over ugerne, men hver uge skal stadig kunne stå alene for et barn der er nyt.
- Uge 13: **showcase**, hvor børnene viser deres projekter.
- Session: **2 timer inkl. 20 min pause**, gruppestørrelse 6-10 pirater (bekræftet, se `design-hold/index.md`).

Hver uges materiale skal indeholde:
1. Overskrift + fængende pitch (1-2 sætninger)
2. Mål
3. En **illustration** af det, ugen bygger — en simpel inline SVG (ingen eksterne billedlicenser at holde styr på) der viser målet/formen, ikke kun tekst
4. Trin-for-trin øvelse, konkret nok til at en frivillig kan undervise direkte efter den
5. **Ekstra udfordringer** — 2-4 valgfrie, sværere opgaver til pirater der bliver hurtigt færdige med kerneøvelsen
6. "✅ Færdig når..." — synligt succeskriterie, inkl. en linje om ekstraudfordringer hvis der var tid
7. Noter (tomt felt til underviserens egne erfaringer)
8. Reference — links til officielle, verificerede kilder (Tinkercad Learn, kodeklubben.dk, Coding Pirates designguide m.fl.)

**Ikke** længere en fast del af skabelonen: Materialer-liste og en tidsopdelt Session-outline-tabel. Underviseren planlægger selv logistik/timing ud fra Trin-for-trin øvelsen og Ekstra udfordringer — siderne skal ikke gentage praktisk mødeforberedelse.

Se `docs/autumn-2026/design-hold/week-01-opsaetning/index.md` som skabelon for struktur og niveau.

## Arbejdsgang for Claude Code
- Slå altid officielle, opdaterede kilder op, når du foreslår værktøjer, tutorials eller links — opfind ikke indhold fra hukommelsen.
- Følg repoets eksisterende mappestruktur og filnavngivning for nye uger/sider (`docs/autumn-2026/design-hold/week-NN-navn/index.md`).
- Ved manglende info (udstyr, hvilken detalje en given uge dækker): spørg kort, eller lav en tydeligt markeret antagelse og forklar den.
- Filer med lokale stier fra en tidligere Claude Desktop-session (fx `/mnt/user-data/outputs/...`) findes ikke i dette repo — flag det og foreslå en erstatning frem for at antage filen findes.
- `mkdocs.yml` har stadig placeholder-URL'er (`REPLACE-WITH-YOUR-GITHUB-USERNAME`) — ret til `cprhub`, når du alligevel redigerer filen.
- `docs/assets/logo.png` og `favicon.png` mangler stadig (kun en README der beskriver kravene) — flag manglen frem for at antage de findes.
