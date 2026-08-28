# SESSION 3 · FLIPPEREN — MEKANISK DESIGN

Sidste session mødte vi de fem store udfordringer i projektet. I dag går vi i gang med den første: **flipperen**. Flipperens vigtigste job er at sparke kuglen tilbage op på banen, så den bliver i spil — uden flippere ville kuglen bare trille ud forneden, og spillet var slut. Vi designer selve flipper-armen i Tinkercad, klar til at blive 3D-printet og senere sat i bevægelse.

## Mål

- Alle pirater har selv prøvet et web-pinball-spil, og lagt mærke til at flipperens job er at sparke kuglen op på banen igen — en vigtig del af selve spillet
- Alle forstår, i grove træk, hvordan en rigtig pinball-flipper bevæger sig omkring et fast omdrejningspunkt
- Alle har designet en flipper-arm i Tinkercad: en aflang "pagaj"-form med et hul til en akse i den brede ende
- Alle har testet, at deres flipper kan rotere frit omkring hullet, uden at ramme noget
- Alle har placeret deres flipper-design ved siden af grundbanen fra session 2, for at se om størrelsen passer

<svg viewBox="0 0 300 140" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Skitse af en flipper: en aflang pagajform der roterer omkring et hul i den brede ende, vist i to positioner - hvilestilling og opad slået" style="width:100%;max-width:420px;height:auto;background:#eef6f9;border-radius:8px;padding:12px;box-sizing:border-box;display:block;margin:0 auto;">
  <circle cx="60" cy="90" r="6" fill="#333" />
  <polygon points="54,84 54,96 220,100 232,90 220,80" fill="#25A2CE" opacity="0.5" />
  <circle cx="60" cy="90" r="6" fill="#333" />
  <polygon points="54,84 54,96 190,30 202,20 210,32" fill="#25A2CE" />
  <text x="60" y="115" font-family="sans-serif" font-size="11" fill="#333" text-anchor="middle">Akse-hul</text>
  <text x="230" y="112" font-family="sans-serif" font-size="11" fill="#333" text-anchor="middle" opacity="0.6">Hvilestilling</text>
  <text x="180" y="16" font-family="sans-serif" font-size="11" fill="#333" text-anchor="middle">Opad slået</text>
</svg>

Skitsen herover viser princippet: flipperen er en aflang form, der roterer omkring et fast punkt i den brede ende — ligesom en pagaj, der svinges op og ned. I en rigtig pinball-maskine er det en elektromagnet (solenoid), der trækker armen op; i dag designer vi kun selve formen, ikke det, der får den til at bevæge sig.

!!! example "Screenshot mangler her"
    **Filnavn:** `screenshot.png` (lægges i denne sessions egen mappe, ved siden af `index.md`)

    **Skal vise:** Den færdige flipper-design i Tinkercad-editoren, set skråt oppefra, så både pagaj-formen og akse-hullet i den brede ende er tydeligt synlige.

    Når filen er lagt ind, erstattes denne boks med: `![Flipperens grove form i Tinkercad](screenshot.png)`

## Trin-for-trin øvelse

1. **Prøv det selv først:** spil et par minutter i et af disse gratis web-pinball-spil (se Reference nedenfor for links) — læg særligt mærke til, hvad flipperne gør: de sparker kuglen tilbage op på banen, hver gang den er ved at rulle ud forneden. Det er den vigtigste opgave, vores egen flipper skal kunne løse
2. Opret et nyt design, og navngiv det efter vores faste struktur: `CPR-[dit navn]-Flipper` (se session 1, hvis du er i tvivl om hvordan)
2. Byg selve **armen**: brug en aflang, tynd kasse eller en trekantet form (**Shapes → Polygon**, tilpasset til 3-4 hjørner), der er smallest i den ene ende og bredest i den anden — det er selve flipperen, kuglen skal ramme. Sigt efter en længde på ca. **60-80 mm**, så den passer i forhold til grundbanen (som er ca. 281 × 410 mm)
3. I den **brede ende** af armen: tilføj en cylinder, sæt den til **Hole**, og placér den centreret i enden — det bliver hullet, flipperen senere skal rotere omkring på en akse. Lav hullet ca. **4-5 mm** i diameter, så det passer til en tynd akse eller bolt
4. Brug **Align** til at centrere hullet præcist i den brede ende af armen
5. Marker arm og hul sammen, og brug **Group**, så hullet skæres ud og flipperen bliver ét samlet objekt
6. **Test rotationen:** dupliker din flipper (Ctrl/Cmd+D), og brug **Rotate**-værktøjet på kopien til at dreje den ca. 40-50 grader omkring omdrejningspunktet i akse-hullet — forestil dig, at det er sådan den bevæger sig, når den slår op. Sørg for, at den ikke ville ramme noget i vejen
7. Åbn din grundbane-kopi fra session 2 i et andet vindue eller faneblad, og sammenlign størrelsen — er din flipper passende stor i forhold til banen? Juster med **Scale**, hvis den er alt for stor eller lille
8. Læg mærke til det markerede bælte i **højre side** af grundbanen — det er reserveret til startskuddet, som vi designer i en senere session. Placér ikke din flipper der
9. Gem designet

!!! note "Vi bygger ikke selve mekanismen i dag"
    I dag designer vi kun formen og akse-hullet. Hvordan flipperen faktisk skal drives (fjeder, gummibånd, eller senere motor via micro:bit) kigger vi på i en senere session, når elektronikken kommer ind i billedet.

## Ekstra udfordringer

Blevet færdig med kernedelen, og der er stadig tid tilbage? Prøv en eller flere af disse:

1. **To flippere:** brug **Mirror**-værktøjet til at lave en spejlvendt kopi af din flipper, så du har et venstre- og et højre-par, ligesom på en rigtig pinball-maskine
2. **Bedre grib:** tilføj en let ophøjet kant eller riller ovenpå flipperen, så kuglen får bedre "grib", når den rammes
3. **Buet form:** prøv at lave armen let buet i stedet for helt lige, og tænk over, hvordan det kan ændre den retning, kuglen bliver sendt i
4. **Skitsér drivkraften:** tegn (på papir eller i Tinkercad) din egen idé til, hvordan flipperen skal sættes i bevægelse senere — det behøver ikke være rigtigt endnu, bare en idé vi kan vende tilbage til

## ✅ Færdig når...

- Din flipper er én samlet form (Group) med et akse-hul i den brede ende
- Du har testet rotationen med en dupliceret, drejet kopi, og den rammer ikke noget i vejen
- Du har sammenlignet størrelsen med din grundbane fra session 2
- Filen er navngivet efter vores faste struktur
- **Hvis der var tid:** du har prøvet mindst én ekstra udfordring

## Noter

*(Tomt felt til underviserens egne erfaringer efter sessionen)*

## Reference

- [Pinball FRVR](https://pinball.frvr.com/) — gratis, spilbart direkte i browseren, ingen download. God til at prøve flipperne selv
- [3D Pinball: Space Cadet (ClassicReload)](https://classicreload.com/win9x-3d-pinball-space-cadet.html) — den klassiske Windows-pinball, spilbar direkte i browseren
- [Rotate It](https://www.tinkercad.com/learn/overview/OIOV5J4JK10UYFU) — officiel Tinkercad-lektion om Rotate-værktøjet
- [Align It](https://www.tinkercad.com/learn/overview/OF8ZOFPL1W5N9DS) — officiel Tinkercad-lektion om Align-værktøjet
- [How Do Pinball Flippers Work? (Simple Explanation)](https://pinballcastle.com/how-do-pinball-flippers-work/) — letforståelig forklaring af den rigtige flipper-mekanisme
