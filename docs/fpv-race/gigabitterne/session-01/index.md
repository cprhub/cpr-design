# SESSION 1 · OPSÆTNING — FÅ LIV I ESP32-S3

Før en racerbil kan køre, skal den have en hjerne. I dag installerer vi værktøjerne, sender vores første program ned i et **ESP32-S3**, og får det til at blinke og tale til os. De erfarne går et skridt videre og får den første del af rattet til at virke.

## Mål

- Alle pirater har installeret Arduino IDE og ESP32-pakken på deres egen computer
- Alle kan vælge det rigtige board og den rigtige port og uploade et program
- Alle har fået ESP32-S3 til at blinke med sin indbyggede lampe og skrive en besked i **Serial Monitor**
- Erfarne pirater har læst et potentiometer (det kommende rat) og set tallene ændre sig

## Trin-for-trin øvelse

### Fælles start — installer værktøjerne

1. Download og installer **Arduino IDE 2** fra [arduino.cc/en/software](https://www.arduino.cc/en/software) (Windows eller Mac)
2. Åbn Arduino IDE. Klik på **Boards Manager**-ikonet i venstre side, søg efter `esp32`, og installer **esp32 by Espressif Systems**. Det tager et par minutter — en god pause til at pakke boardet ud
3. Sæt dit **ESP32-S3 DevKitC-1** til computeren med et USB-C-kabel. Boardet har to USB-C-stik — brug det, der er mærket **UART** (eller COM)
4. Vælg board: **Tools → Board → esp32 → ESP32S3 Dev Module**
5. Vælg port: **Tools → Port** — vælg den port, der dukkede op, da du satte boardet til

!!! tip "Kan computeren ikke finde boardet?"
    Prøv et andet USB-kabel — nogle kabler kan kun lade, ikke sende data. På Windows kan det være nødvendigt at installere en driver til USB-chippen på boardet. Spørg underviseren.

### Spor A — Første program: blink og hils

ESP32-S3 DevKitC-1 har en lille **farvelampe** (RGB-LED) indbygget. Den styrer vi med `rgbLedWrite(RGB_BUILTIN, rød, grøn, blå)`, hvor hver farve er et tal fra 0 til 255.

1. Lav et nyt program (**File → New Sketch**), og skriv:

    ```cpp
    void setup() {
      Serial.begin(115200);
    }

    void loop() {
      rgbLedWrite(RGB_BUILTIN, 0, 0, 64);   // blå
      Serial.println("Ahoy fra ESP32-S3!");
      delay(500);
      rgbLedWrite(RGB_BUILTIN, 0, 0, 0);    // slukket
      delay(500);
    }
    ```

2. Klik **Upload** (pilen øverst til venstre). Vent til der står "Done uploading"
3. Lampen blinker blåt! Åbn **Serial Monitor** (forstørrelsesglasset øverst til højre), og sæt hastigheden til **115200 baud**. Nu kan du se boardets hilsen
4. Prøv at ændre farven: `64, 0, 0` er rød, `0, 64, 0` er grøn. Hvad giver `64, 64, 0`?
5. Prøv at ændre `delay(500)` til et mindre tal. Hvad sker der?

!!! example "Foto mangler her"
    **Filnavn:** `foto-blink.png` (lægges i denne sessions egen mappe, ved siden af `index.md`)

    **Skal vise:** Et ESP32-S3 DevKitC-1 sat til en bærbar med USB-C-kabel i UART-stikket, med den indbyggede lampe lysende blå, og Serial Monitor i Arduino IDE i baggrunden med "Ahoy fra ESP32-S3!" skrevet flere gange.

    Når filen er lagt ind, erstattes denne boks med: `![ESP32-S3 blinker og hilser i Serial Monitor](foto-blink.png)`

### Spor B — Erfarne pirater: det første rat

Rattet i vores konsol er et **potentiometer**: en drejeknap, hvor midterbenet giver en spænding, der ændrer sig, når man drejer. ESP32-S3 måler det som et tal mellem 0 og 4095.

1. Sæt et potentiometer i et breadboard. Forbind **venstre ben til 3.3V**, **højre ben til GND** og **midterbenet til GPIO 4**
2. Skriv:

    ```cpp
    const int ratPin = 4;

    void setup() {
      Serial.begin(115200);
    }

    void loop() {
      int raaRat = analogRead(ratPin);              // 0-4095
      int vinkel = map(raaRat, 0, 4095, 60, 120);  // servo-grader
      Serial.print("Rat: ");
      Serial.print(raaRat);
      Serial.print("   Vinkel: ");
      Serial.println(vinkel);
      delay(100);
    }
    ```

3. Upload, åbn Serial Monitor, og drej på knappen. Tallene ændrer sig!
4. `map()` omregner rattets 0-4095 til **60-120 grader** — det er de vinkler, forhjulene skal dreje mellem. 90 er ligeud
5. Prøv **Tools → Serial Plotter** i stedet. Nu kan du se rattet som en kurve

## Ekstra udfordringer

Blevet færdig før tiden? Prøv en eller flere af disse:

1. **Regnbuelampe:** få lampen til at skifte langsomt mellem alle farver ved hjælp af en `for`-løkke
2. **Rat-lampe:** få lampen til at lyse rød, når rattet drejes til venstre, grøn i midten og blå til højre
3. **Tre potentiometre:** tilføj speeder (GPIO 5) og bremse (GPIO 6), og skriv alle tre tal ud på én linje
4. **Kamera-boardet:** sæt bilens ESP32-S3 med kamera til, og upload blink-programmet til det også. Husk at vælge den rigtige port

## ✅ Færdig når...

- Arduino IDE og esp32-pakken er installeret på din computer
- Du har selv uploadet et program, og lampen blinker
- Du kan se boardets besked i Serial Monitor
- **Erfarne:** du kan dreje på potentiometret og se vinklen gå fra 60 til 120
- **Hvis der var tid:** du har prøvet mindst én ekstra udfordring

!!! tip "Næste gang: rat og pedaler"
    I session 2 bygger vi alle tre styregrej på breadboardet — rat, speeder og bremse — og regner ud, om bilen skal køre frem, bakke eller holde stille.

## Noter

*(Tomt felt til underviserens egne erfaringer efter sessionen)*

## Reference

- [Arduino IDE](https://www.arduino.cc/en/software) — download til Windows og Mac
- [Arduino-ESP32: installation](https://docs.espressif.com/projects/arduino-esp32/en/latest/installing.html) — Espressifs officielle vejledning til ESP32-pakken
- [ESP32-S3-DevKitC-1](https://docs.espressif.com/projects/esp-dev-kits/en/latest/esp32s3/esp32-s3-devkitc-1/index.html) — boardets pinout og USB-stik
- [Espressifs BlinkRGB-eksempel](https://github.com/espressif/arduino-esp32/blob/master/libraries/ESP32/examples/GPIO/BlinkRGB/BlinkRGB.ino) — officielt eksempel på `rgbLedWrite` og `RGB_BUILTIN`
- [Arduino: analogRead](https://docs.arduino.cc/language-reference/en/functions/analog-io/analogRead/) og [map](https://docs.arduino.cc/language-reference/en/functions/math/map/)
- [FPV Car Race byggevejledning](../../byggevejledning/index.md) — hele projektets kode og ledningsdiagram
