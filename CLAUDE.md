# Coding Pirates Rødovre – undervisningsmateriale

## Opgaven
Dette repo indeholder undervisningsmateriale til **Coding Pirates Rødovre**, samlet ét sted for flere hold. Formålet med dette projekt er at hjælpe med at skrive, strukturere og vedligeholde det materiale, en frivillig underviser bruger direkte i undervisningen.

Sitet bygges med **MkDocs Material** og udgives via GitHub Pages (se `.github/workflows/deploy.yml`). Følg den eksisterende mappestruktur og front matter — se `README.md` for detaljer.

Hvert hold har sin egen mappe direkte under `docs/` (ikke sæson-opdelt):
- `docs/juletog/` — Design-holdets efterår 2026-forløb, se afsnittet "Juletog" nedenfor
- `docs/pinball/` — Pinball-holdets efterår 2026-forløb, se afsnittet "Pinball" nedenfor

Reference/inspiration (anden holdleders materiale, samme forening): https://itsgauravsaxena.github.io/cpr-microbit/ — brug den til at forstå tone, opbygning og niveau.

## Målgruppe (gælder for alt indhold)
- Børn på **10-12 år**.
- **Altid begynderniveau** — ingen forudsætninger antages, heller ikke fra tidligere sessioner, da nye pirater kan komme til undervejs. Byg kort genopfriskning ind, hvis en session bygger på noget tidligere.
- Sprog: **dansk er kildesprog** (engelsk oversættelse findes via i18n-pluginnet, når den er lavet). Tone: legende, opmuntrende "sørøver"-stil som resten af Coding Pirates — kort, konkret, lidt humor. **Ingen emojis** (heller ikke i overskrifter/pitch) — brug ordvalg og "!" til at bære tonen i stedet. Undtagelsen er ✅ som fast statusikon i "✅ Færdig når..."-overskrifter og status-kolonner, det er struktur, ikke tone. Undgå at virke nedladende for 12-årige.
- **Terminologi:** brug altid **"session"**, aldrig "uge"/week — mappenavne følger `session-NN(-navn)/index.md`. Denne regel gælder alle hold i dette repo.

## Software-krav (ufravigeligt, gælder alle hold)
- Undervisning foregår på **Windows og Mac** — ingen løsninger der kræver iPad/Chromebook.
- **Kun gratis eller open source programmer.** Aldrig noget der kræver betalt licens/abonnement/"pro"-version for at gennemføre øvelsen.
  - Hvis et værktøj har både gratis og betalt niveau: undersøg og bekræft, at gratis-niveauet er nok til øvelsen — ellers find et alternativ.
- Ved tvivl om pris eller platformsunderstøttelse: **slå det op**, gæt ikke.

## Fælles skabelon for en sessions materiale
Hver sessions materiale skal indeholde:
1. Overskrift + fængende pitch (1-2 sætninger)
2. Mål
3. En **illustration** af det, sessionen bygger. Standarden er et rigtigt screenshot/foto: da Claude Code ikke har adgang til en fungerende browser eller kamera, indsæt i stedet en tydelig "Screenshot/foto mangler her"-boks (`!!! example`) med **Filnavn** (simpelt, i sessionens egen mappe, fx `screenshot.png`) og **Skal vise** (præcis beskrivelse af vinkel/indhold), plus den færdige `![...]()`-linje der skal indsættes når filen er lagt ind. Brug kun en selvlavet inline SVG som illustration, når det ikke er et screenshot/foto af selve øvelsen (fx en stil-reference)
4. Trin-for-trin øvelse, konkret nok til at en frivillig kan undervise direkte efter den
5. **Ekstra udfordringer** — 2-4 valgfrie, sværere opgaver til pirater der bliver hurtigt færdige med kerneøvelsen
6. "✅ Færdig når..." — synligt succeskriterie, inkl. en linje om ekstraudfordringer hvis der var tid
7. Noter (tomt felt til underviserens egne erfaringer)
8. Reference — links til officielle, verificerede kilder

**Ikke** en fast del af skabelonen: Materialer-liste og en tidsopdelt Session-outline-tabel. Underviseren planlægger selv logistik/timing ud fra Trin-for-trin øvelsen og Ekstra udfordringer — siderne skal ikke gentage praktisk mødeforberedelse.

---

## Juletog (Design-holdet)
Design-holdets efterår 2026-forløb er **ét sammenhængende 3D-design-projekt**, ikke en blanding af discipliner: piraterne designer og 3D-printer deres eget **LEGO-kompatible juletog** i **Tinkercad**, inspireret af det klassiske LEGO-juletog. Toget skal kunne køre på rigtige LEGO-skinner (sporvidde ca. 37,5 mm), så forløbet inkluderer også at måle, designe efter mål, og teste/justere print undervejs. Se den fulde sessionsoversigt i `docs/juletog/index.md`.

- **Software:** Tinkercad (gratis).
- **Udstyr:** Egne bærbare (Windows/Mac) + **Bambu Lab A1 Mini** (holdets flerfarvede printer, bruges løbende, maks. 1 time pr. print) + **TekX-printere** (eksterne, én farve ad gangen, til store funktionelle dele — besøg i session 7, 10 og 11).
- **Metode:** Hver del af toget designes som sin egen fil/objekt, så den kan printes/males i egen farve.
- **13-sessioners struktur:** Session 1 er en "quick win" — noget der virker med det samme og giver mestringsfølelse. Gradvist stigende sværhedsgrad, men hver session skal stadig kunne stå alene for et barn der er nyt. Session 13: **showcase**, hvor børnene viser deres projekter.

Fremtidige sæsoner/hold kan sagtens dække andre design-discipliner (grafisk design, spildesign, web/UI) — men det er *ikke* efterår 2026-forløbet, og skal ikke blandes ind i den eksisterende sessionsoversigt uden eksplicit aftale.

### Filnavne-konvention (ufravigeligt, kun Juletog)
Alle Tinkercad-designs skal navngives **`CPR-[elevnavn]-[figurnavn]`** (fx `CPR-Anna-Lokomotiv`). Det er ikke kun ordenssans — det er sådan TekX kan finde og printe de rigtige filer. Konventionen er undervist i sin fulde form i session 1 (`docs/juletog/session-01-opsaetning/index.md`, afsnittet "Filnavne — vores faste struktur", inkl. hvordan man omdøber et design i Tinkercad). **Hver efterfølgende sessions Trin-for-trin øvelse skal minde om konventionen** i det trin hvor et nyt design oprettes/navngives — kort reference er nok (fx "navngiv efter vores faste struktur: `CPR-[dit navn]-X`"), det behøver ikke gentage hele forklaringen.

Se `docs/juletog/session-01-opsaetning/index.md` som skabelon for struktur og niveau.

**Status:** Session 1-2 er skrevet. Session 3-13 mangler stadig (kun titler i sessionsoversigt-tabellen i `docs/juletog/index.md`).

---

## Pinball (Pinball-holdet)
Pinball-holdet skal bygge en **fysisk pinball-maskine** over **max 13 sessioner** (efterår 2026, ikke nødvendigvis alle 13 bruges). Se `docs/pinball/index.md`. Hver session er **2 timer inkl. 20 min pause** (bekræftet). Der er **ikke** nødvendigvis 13 sessioner — 13 er loftet, det faktiske antal fastlægges ud fra hvor mange sessioner byggeriet kræver. Hvis det endelige antal bliver mindre end 13, ryd de ubrugte `docs/pinball/session-NN/`-mapper op i stedet for at lade dem stå som tomme skabeloner.

**Målgruppe/gruppestørrelse:** Samme som Juletog — 10-12 år, 6-10 pirater (plus Microbit-holdets børn på elektronik-sessionerne, se nedenfor).

**Byggemetode (bekræftet):**
- **3D-print** — samme udstyrsmønster som Juletog: egne bærbare + **Bambu Lab A1 Mini** (holdets flerfarvede printer, løbende brug, maks. 1 time pr. print) + **TekX-printere** (eksterne, store funktionelle dele).
- **Laser cut** — Coding Pirates har sin egen laser cutter, men det er en **Class 4-laser**, som børn ikke må betjene. Laser cutning af flade paneldele foregår derfor af **læreren mellem sessionerne**: børnene designer/måler op i en session, læreren skærer, og det færdige resultat er klar til næste session. Dette skal fremgå tydeligt i enhver session hvor laser cut indgår, så underviseren husker at forberede det inden næste gang.
- **Elektronik: micro:bit**, i **samarbejde med Microbit-holdet** — et andet Coding Pirates Rødovre-hold med sin egen holdleder (samme som står bag søsterprojektet `cpr-microbit`, https://itsgauravsaxena.github.io/cpr-microbit/). Design-holdet bygger selve maskinen (mekanik/kabinet), Microbit-holdet designer elektronikken (sensorer, point, lys/lyd) og kommer ind på de sessioner der er markeret til det. **Denne fordeling og de konkrete elektronik-sessioners indhold er IKKE bekræftet med Microbit-holdets leder endnu** — behandl dem som en tydeligt markeret antagelse i indholdet, indtil det er koordineret.

**Foreløbig sessionsoversigt** (antagelse, se `docs/pinball/index.md` for den fulde tabel med `!!! note`-markering): session 1 er introduktion til Tinkercad (samme som Juletogs session 1, øvede laver Kaptajn Hack med QR-kode i nakken, se dens egen status nedenfor), session 2-6 er fysisk design/bygning (kabinet, flippers, bumpers, laser cut, samling), session 7-11 er micro:bit-elektronik (i samarbejde med Microbit-holdet), session 12 er finish, session 13 er showcase.

**Status:** Session 1 er skrevet. Session 2-13 mangler stadig (kun titler i sessionsoversigt-tabellen i `docs/pinball/index.md`).

## Arbejdsgang for Claude Code
- Slå altid officielle, opdaterede kilder op, når du foreslår værktøjer, tutorials eller links — opfind ikke indhold fra hukommelsen.
- Følg repoets eksisterende mappestruktur og filnavngivning for nye sessioner/sider (`docs/juletog/session-NN-navn/index.md` eller `docs/pinball/session-NN/index.md`).
- Ved manglende info (udstyr, hvilken detalje en given session dækker): spørg kort, eller lav en tydeligt markeret antagelse og forklar den.
- Filer med lokale stier fra en tidligere Claude Desktop-session (fx `/mnt/user-data/outputs/...`) findes ikke i dette repo — flag det og foreslå en erstatning frem for at antage filen findes.
