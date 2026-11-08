# SESSION 1 · VELKOMMEN TIL LAYERLING

Nyt skib, ny værktøjskasse! I dag skifter vi til **Layerling** — et gratis 3D-designprogram i browseren, der virker som Tinkercad, men kan meget mere. Og de erfarne pirater laver det første stykke af racerbilen: **en nummerplade med jeres startnummer**.

## Mål

- Alle pirater kan åbne Layerling, sætte det på dansk og oprette et nyt design
- Alle kan placere former, ændre størrelsen, lave huller og gruppere
- Alle kan gemme en sikkerhedskopi af deres design som en `.lyl`-fil
- Erfarne pirater har lavet en nummerplade med afrundede kanter og tekst, klar til print

## Filnavne — vores faste struktur

**Alle designs og alle filer, vi eksporterer, skal navngives efter samme struktur, hele forløbet igennem:**

```
CPR-[elevnavn]-[navn på delen]
```

Fx `CPR-Anna-Nummerplade`. Det er sådan TekX kan finde og printe de rigtige filer for os, så hvis navnet mangler eller er forkert, kan tingene ikke printes. **Vi gør det hver session**, så det bliver en vane.

**Sådan omdøber du et design i Layerling:**

1. Gå til **startsiden** (der hvor alle dine designs ligger som små billeder)
2. Åbn menuen på dit design, og vælg **Omdøb**
3. Skriv det nye navn efter strukturen: `CPR-[dit navn]-[delens navn]`

Når du **eksporterer** en fil (se nedenfor), står navnet i feltet **Filnavn** øverst i eksport-vinduet. Tjek at det også følger strukturen.

## Gem en sikkerhedskopi — hver gang!

Layerling gemmer automatisk, men **kun i browseren på din egen computer**. Hvis browserens data bliver slettet, eller du skifter computer, er designet væk. Derfor slutter vi hver session sådan her:

1. Klik **Eksportér** (eller tryk Ctrl+E)
2. Vælg formatet **LYL**
3. Klik **Gem layerling-design**, og gem filen i en mappe, du kan finde igen (fx en mappe der hedder `Coding Pirates`)

Filen ender på `.lyl`. Den kan åbnes igen på en hvilken som helst computer.

## Trin-for-trin øvelse

### Fælles start — alle pirater

1. Åbn [layerling.com](https://layerling.com/) i browseren. Der skal ikke laves en konto
2. Sæt programmet på dansk: vælg **Dansk** under **Indstillinger** på startsiden (eller i sprogvalget øverst i editoren)
3. Klik **Opret nyt 3D-design**. Du ser nu en tom arbejdsplade
4. Se dig omkring med musen: træk med **højre** museknap for at dreje udsigten, træk med **midterste** knap for at flytte den, og rul med hjulet for at zoome

Holdet deles derefter i to spor efter erfaring:

### Spor A — Nye pirater: kassen med hullet

Det her er Layerlings egen første øvelse, og den lærer dig de vigtigste greb:

1. Klik **Tilføj form**, vælg **Kasse**, og klik på arbejdspladen for at placere den
2. Ret kassens mål i panelet til højre, fx 30 x 30 x 20 mm
3. Placér en **Cylinder** midt i kassen. Gør den højere end kassen, så den stikker op over toppen
4. Vælg cylinderen, og skift den fra **Solid** til **Hul** i panelet til højre
5. Vælg både kassen og cylinderen (hold Shift nede, mens du klikker), og klik **Gruppér**. Nu er der et hul tværs gennem kassen!
6. Prøv selv: flyt, drej og skalér en ny form. Hold **Alt** nede, mens du trækker i en form, så laver du en kopi
7. Omdøb designet til `CPR-[dit navn]-Kasse`, og gem en sikkerhedskopi (se ovenfor)

Kender du Tinkercad i forvejen? Så vil du genkende det meste: arbejdspladen, solid og hul, gruppér, Alt-træk for at kopiere.

### Spor B — Erfarne pirater: bilens nummerplade

Hver racerbil skal have sin egen **nummerplade** med holdets startnummer. Den er lille, hurtig at printe, og den bliver det første stykke af bilen.

!!! example "Screenshot mangler her"
    **Filnavn:** `screenshot-spor-b.png` (lægges i denne sessions egen mappe, ved siden af `index.md`)

    **Skal vise:** Den færdige nummerplade i Layerling set skråt oppefra: en flad plade med afrundede kanter, med "CPR" og et startnummer i hævet tekst i en anden farve.

    Når filen er lagt ind, erstattes denne boks med: `![Færdig nummerplade i Layerling](screenshot-spor-b.png)`

1. Opret et nyt design, og omdøb det til `CPR-[dit navn]-Nummerplade`
2. Tilføj en **Kasse** på ca. 40 x 15 x 2 mm. Det er selve pladen
3. Rund pladens hjørner: vælg pladen, klik **Rund** i værktøjslinjen, vælg **Lodrette kanter**, sæt **Radius** til 2 mm, og klik **Anvend**. Du kan altid ændre eller fjerne afrundingen igen bagefter
4. Tilføj en **Tekst**-form. Skriv `CPR` og jeres startnummer (spørg underviseren, hvilket nummer jeres bil har)
5. Gør teksten ca. 1 mm høj, og læg den oven på pladen. Brug **Justér** til at centrere den
6. Giv teksten en anden farve end pladen
7. Vælg plade og tekst, og brug **Bundt** (Ctrl+B). Så hænger de sammen, men beholder hver sin farve, når vi printer i to farver
8. Eksportér nummerpladen som **3MF** — det format beholder farverne. Tjek at **Filnavn** følger vores struktur
9. Gem til sidst en sikkerhedskopi som `.lyl`

!!! note "Nummerpladen printes senere"
    Nummerpladen printes i to farver på Bambu Lab A1 Mini, når underviseren har samlet alle filerne. Hvor den skal sidde på bilen, finder vi ud af, når karosseriet tager form.

## Ekstra udfordringer

Blevet færdig før tiden? Prøv en eller flere af disse:

**Spor A (nye pirater):**

1. Lav en terning: en kasse med afrundede kanter (**Rund** → **Alle skarpe kanter**) og små cylindre som huller til øjnene
2. Byg en lille figur af 4-5 forskellige former uden en vejledning
3. Prøv Layerlings egen [vejledning på dansk](https://layerling.com/vejledning/index.html), kapitlet om placering af former

**Spor B (erfarne pirater):**

1. Lav to små huller i nummerpladen, så den kan skrues eller bindes fast på bilen
2. Lav en kasse om til en lille æske: vælg kassen, klik **Hul** i værktøjslinjen (ikke Hul-knappen i panelet til højre), sæt **Vægtykkelse** til 2 mm, lad **Top** stå som åben side, og klik **Anvend**
3. Find formen **USB-C** i formbiblioteket, og lav et hul til et USB-C-stik i en plade. Den slags skal vi bruge til elektronikbakken senere

## ✅ Færdig når...

- Du kan åbne Layerling selv og oprette et nyt design
- Du har prøvet at flytte, dreje, skalere, lave et hul og gruppere
- Du har gemt en sikkerhedskopi som `.lyl`, og den har det rigtige navn
- **Erfarne:** din nummerplade er færdig og eksporteret som 3MF med det rigtige filnavn
- **Hvis der var tid:** du har prøvet mindst én ekstra udfordring

!!! tip "Næste gang: mål op!"
    I session 2 får vi Gigabitternes målliste over chassiset og elektronikken. Vi laver simple **dummy-klodser** af hver del i Layerling, så vi kan designe bilen rundt om dem. Tag gerne en skydelære med, hvis du har en.

## Noter

*(Tomt felt til underviserens egne erfaringer efter sessionen)*

## Reference

- [Layerling](https://layerling.com/) — selve programmet (gratis, open source, ingen konto)
- [Layerling-vejledning på dansk](https://layerling.com/vejledning/index.html) — officiel brugervejledning trin for trin
- [Kom godt i gang](https://layerling.com/vejledning/getting-started.html) — den første øvelse med kassen og hullet
- [Filer, lagring og deling](https://layerling.com/vejledning/files-and-saving.html) — om sikkerhedskopier og eksport
- [Layerling på GitHub](https://github.com/henmedia/layerling) — kildekoden (AGPL-3.0)
