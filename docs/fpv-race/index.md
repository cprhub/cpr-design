# FPV CAR RACE

Et fælles projekt for to hold: vi bygger vores egne **FPV-racerbiler** — biler med et kamera foran, som man styrer med rat og pedaler, mens man ser verden fra førersædet gennem et par hjemmebyggede videobriller. FPV betyder *First Person View*: du ser det, bilen ser.

- **Design-holdet** designer og 3D-printer **selve bilen** i [Layerling](https://layerling.com/) — karosseri, holdere til elektronikken, kamerabeslag og pynt.
- **Gigabitterne** bygger **styringen og videoen** — elektronikken og koden i bilen, rattet, pedalerne og videobrillerne.

Til sidst mødes de to hold, sætter elektronikken i karrosserierne og kører et rigtigt **Grand Prix**.

*Session: 2 timer inkl. 20 min pause · Udstyr: egne bærbare (Windows/Mac) + Bambu Lab A1 Mini + TekX-printere · Kun gratis/open source software (Layerling, Arduino IDE)*

!!! note "Foreløbig plan"
    Sessionsoversigterne er en **foreløbig antagelse**: sæson (forår 2027), antal sessioner (op til 13), Gigabitternes alder/niveau og hvilke sessioner holdene er sammen på er ikke endeligt aftalt endnu. Det samme gælder antallet af biler (vi regner med én bil pr. gruppe på 2-3 pirater).

## De to hold

| Hold | Bygger | Værktøj | Oversigt |
|---|---|---|---|
| **Design-holdet** | Bilens karosseri, elektronikbakke, kameraholder, pynt | Layerling + 3D-print | [Design-holdets sessioner](design/index.md) |
| **Gigabitterne** | Elektronik og kode i bil og konsol, rat, pedaler, videobriller | Arduino IDE + ESP32-S3 + lodning (med voksen) | [Gigabitternes sessioner](gigabitterne/index.md) |

Den komplette **[byggevejledning](byggevejledning/index.md)** (indkøbsliste, ledningsdiagram og al koden) er fælles for begge hold og er primært til underviserne.

## Sådan hænger det sammen

```
   KONSOLLEN (Gigabitterne)                         BILEN (begge hold)
 +---------------------------+                 +---------------------------+
 | Rat + speeder + bremse    |  styring (UDP)  | Servo (forhjul)           |
 | ESP32-S3 DevKitC-1        | --------------> | Motor (baghjul)           |
 | 2 skærme i VR-brillen     | <-------------- | ESP32-S3 med kamera       |
 | Powerbank                 |   video (WiFi)  | Batteri + 5V-regulator    |
 +---------------------------+                 | Karosseri (Design-holdet) |
                                               +---------------------------+
```

Bilen laver sit eget lille WiFi-net med sit eget navn (fx `CPR-BIL-1`). Konsollen kobler sig på det, sender rattets og pedalernes position 20-25 gange i sekundet og modtager kamerabilledet, som den viser på begge skærme i brillerne.

## Aftaler mellem holdene

Design-holdet kan kun lave en bil, der passer, hvis de kender de rigtige mål på elektronikken. Derfor:

1. **Gigabitterne afleverer en målliste** (skydelære, i mm) over de dele, der skal sidde i bilen: kamera-boardet, motordriveren, 5V-regulatoren, batteriholderen og chassiset med hjul, servo og motor. Gerne inden Design-holdets session 2.
2. **Design-holdet laver plads til ledninger og stik**: USB-C-stikket på kamera-boardet skal kunne nås uden at skille bilen ad, og kameraet skal kunne se frem uden at karosseriet er i vejen.
3. **Sammen** på de fælles sessioner (se oversigterne): elektronikken flytter ind i karosseriet, bilen testkøres og justeres, og til sidst Grand Prix.

## Sikkerhed

- **Lodning** sker kun med en voksen ved siden af.
- **Li-ion-batterierne (18650)** skal være *beskyttede* celler og lades med en rigtig lader, aldrig uden opsyn. Et batteri, der er bulet, varmt eller lugter, tages ud med det samme.
- **Bilen har et indbygget nødstop** i koden: mister den forbindelsen til rattet i et halvt sekund, stopper motoren af sig selv.
