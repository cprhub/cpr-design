# Coding Pirates Rødovre – Design-hold undervisningsmateriale

## Opgaven
Dette repo indeholder undervisningsmateriale til **Coding Pirates Rødovre's Design-hold** — et **13-sessioners forløb**. Formålet med dette projekt er at hjælpe med at skrive, strukturere og vedligeholde det materiale, en frivillig underviser bruger direkte i undervisningen.

Reference/inspiration (anden holdleders materiale, samme forening): https://itsgauravsaxena.github.io/cpr-microbit/ — brug den til at forstå tone, opbygning og niveau, men indholdet her er en anden disciplin (3D-design, ikke micro:bit).

Sitet bygges med **MkDocs Material** og udgives via GitHub Pages (se `.github/workflows/deploy.yml`). Følg den eksisterende mappestruktur og front matter — se `README.md` for detaljer.

## Målgruppe (gælder for alt indhold)
- Børn på **10-12 år**.
- **Altid begynderniveau** — ingen forudsætninger antages, heller ikke fra tidligere sessioner, da nye pirater kan komme til undervejs. Byg kort genopfriskning ind, hvis en session bygger på noget tidligere.
- Sprog: **dansk er kildesprog** (engelsk oversættelse findes via i18n-pluginnet, når den er lavet). Tone: legende, opmuntrende "sørøver"-stil som resten af Coding Pirates — kort, konkret, lidt humor. **Ingen emojis** (heller ikke i overskrifter/pitch) — brug ordvalg og "!" til at bære tonen i stedet. Undtagelsen er ✅ som fast statusikon i "✅ Færdig når..."-overskrifter og status-kolonner, det er struktur, ikke tone. Undgå at virke nedladende for 12-årige.

## Design-holdets indhold
Holdets efterår 2026-forløb er **ét sammenhængende 3D-design-projekt**, ikke en blanding af discipliner: piraterne designer og 3D-printer deres eget **LEGO-kompatible juletog** i **Tinkercad**, inspireret af det klassiske LEGO-juletog. Toget skal kunne køre på rigtige LEGO-skinner (sporvidde ca. 37,5 mm), så forløbet inkluderer også at måle, designe efter mål, og teste/justere print undervejs. Se den fulde sessionsoversigt i `docs/autumn-2026/design-hold/index.md`.

- **Software:** Tinkercad (gratis) — se software-krav nedenfor.
- **Udstyr:** Egne bærbare (Windows/Mac) + **Bambu Lab A1 Mini** (holdets flerfarvede printer, bruges løbende, maks. 1 time pr. print) + **TekX-printere** (eksterne, én farve ad gangen, til store funktionelle dele — besøg i session 7, 10 og 11).
- **Metode:** Hver del af toget designes som sin egen fil/objekt, så den kan printes/males i egen farve.

Fremtidige sæsoner/hold under dette repo kan sagtens dække andre design-discipliner (grafisk design, spildesign, web/UI) — men det er *ikke* efterår 2026-forløbet, og skal ikke blandes ind i den eksisterende sessionsoversigt uden eksplicit aftale.

## Filnavne-konvention (ufravigeligt)
Alle Tinkercad-designs skal navngives **`CPR-[elevnavn]-[figurnavn]`** (fx `CPR-Anna-Lokomotiv`). Det er ikke kun ordenssans — det er sådan TekX kan finde og printe de rigtige filer. Konventionen er undervist i sin fulde form i session 1 (`docs/autumn-2026/design-hold/session-01-opsaetning/index.md`, afsnittet "Filnavne — vores faste struktur", inkl. hvordan man omdøber et design i Tinkercad). **Hver efterfølgende sessions Trin-for-trin øvelse skal minde om konventionen** i det trin hvor et nyt design oprettes/navngives — kort reference er nok (fx "navngiv efter vores faste struktur: `CPR-[dit navn]-X`"), det behøver ikke gentage hele forklaringen.

## Software-krav (ufravigeligt)
- Undervisning foregår på **Windows og Mac** — ingen løsninger der kræver iPad/Chromebook.
- **Kun gratis eller open source programmer.** Aldrig noget der kræver betalt licens/abonnement/"pro"-version for at gennemføre øvelsen.
  - Tinkercad er gratis at bruge til dette formål.
  - Hvis et værktøj har både gratis og betalt niveau: undersøg og bekræft, at gratis-niveauet er nok til øvelsen — ellers find et alternativ.
- Ved tvivl om pris eller platformsunderstøttelse: **slå det op**, gæt ikke.

## Session-struktur (13 sessioner)
- Session 1: en "quick win" — noget der virker med det samme og giver mestringsfølelse.
- Gradvist stigende sværhedsgrad hen over sessionerne, men hver session skal stadig kunne stå alene for et barn der er nyt.
- Session 13: **showcase**, hvor børnene viser deres projekter.
- Session: **2 timer inkl. 20 min pause**, gruppestørrelse 6-10 pirater (bekræftet, se `design-hold/index.md`).

Hver sessions materiale skal indeholde:
1. Overskrift + fængende pitch (1-2 sætninger)
2. Mål
3. En **illustration** af det, sessionen bygger. Standarden er en rigtig Tinkercad-screenshot: da Claude Code ikke har adgang til en fungerende browser der kan logge ind og bygge i Tinkercad, indsæt i stedet en tydelig "Screenshot mangler her"-boks (`!!! example`) med **Filnavn** (simpelt, i sessionens egen mappe, fx `screenshot.png`) og **Skal vise** (præcis beskrivelse af vinkel/indhold), plus den færdige `![...]()`-linje der skal indsættes når filen er lagt ind. Brug kun en selvlavet inline SVG som illustration, når det ikke er et screenshot af en Tinkercad-øvelse (fx en stil-reference til et logo/maskot)
4. Trin-for-trin øvelse, konkret nok til at en frivillig kan undervise direkte efter den
5. **Ekstra udfordringer** — 2-4 valgfrie, sværere opgaver til pirater der bliver hurtigt færdige med kerneøvelsen
6. "✅ Færdig når..." — synligt succeskriterie, inkl. en linje om ekstraudfordringer hvis der var tid
7. Noter (tomt felt til underviserens egne erfaringer)
8. Reference — links til officielle, verificerede kilder (Tinkercad Learn, kodeklubben.dk, Coding Pirates designguide m.fl.)

**Ikke** længere en fast del af skabelonen: Materialer-liste og en tidsopdelt Session-outline-tabel. Underviseren planlægger selv logistik/timing ud fra Trin-for-trin øvelsen og Ekstra udfordringer — siderne skal ikke gentage praktisk mødeforberedelse.

Se `docs/autumn-2026/design-hold/session-01-opsaetning/index.md` som skabelon for struktur og niveau.

## Arbejdsgang for Claude Code
- Slå altid officielle, opdaterede kilder op, når du foreslår værktøjer, tutorials eller links — opfind ikke indhold fra hukommelsen.
- Følg repoets eksisterende mappestruktur og filnavngivning for nye sessioner/sider (`docs/autumn-2026/design-hold/session-NN-navn/index.md`).
- Ved manglende info (udstyr, hvilken detalje en given session dækker): spørg kort, eller lav en tydeligt markeret antagelse og forklar den.
- Filer med lokale stier fra en tidligere Claude Desktop-session (fx `/mnt/user-data/outputs/...`) findes ikke i dette repo — flag det og foreslå en erstatning frem for at antage filen findes.
- `mkdocs.yml` har stadig placeholder-URL'er (`REPLACE-WITH-YOUR-GITHUB-USERNAME`) — ret til `cprhub`, når du alligevel redigerer filen.
- `docs/assets/logo.png` og `favicon.png` mangler stadig (kun en README der beskriver kravene) — flag manglen frem for at antage de findes.
