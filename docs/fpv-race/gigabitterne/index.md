# FPV CAR RACE · GIGABITTERNE

Gigabitternes del af FPV Car Race: vi bygger **styringen og videoen**. Elektronikken og koden i bilen, et rat og to pedaler, og et par hjemmebyggede videobriller med to små skærme, så man ser verden gennem bilens kamera. Design-holdet bygger karosseriet, og til sidst flytter vores elektronik ind i deres biler.

*Session: 2 timer inkl. 20 min pause · Udstyr: egne bærbare (Windows/Mac) + ESP32-S3-boards + elektronik fra [indkøbslisten](../byggevejledning/index.md#indkbsliste) · Kun gratis/open source software (Arduino IDE)*

!!! note "Foreløbig plan"
    Sessionsoversigten er en **foreløbig antagelse** og ikke koordineret med Gigabitternes holdleder endnu — hverken alder/niveau, gruppestørrelse eller hvilke sessioner der er fælles med Design-holdet (markeret "Begge").

## Sessionsoversigt

| Session | Fokus | Hold |
|---|---|---|
| 1 | [Opsætning — få liv i ESP32-S3](session-01/index.md) | Gigabitterne |
| 2 | Rat og pedaler — potentiometre og `analogRead` | Gigabitterne |
| 3 | Servoen — forhjulene drejer | Gigabitterne |
| 4 | Motoren — frem, bak og fart med motordriveren | Gigabitterne |
| 5 | Strøm på bilen — batteri, 5V-regulator og lodning + målliste til Design-holdet | Gigabitterne |
| 6 | Trådløs styring — rattet styrer bilen over WiFi, med nødstop | Gigabitterne |
| 7 | Kameraet — billeder fra bilen | Gigabitterne |
| 8 | Skærmene — få liv i de to ST7789-skærme | Gigabitterne |
| 9 | Video i brillerne — kamerabilledet på begge skærme | Gigabitterne |
| 10 | Elektronikken flytter ind i bilen | Begge |
| 11 | Testkørsel og justering | Begge |
| 12 | Konsollen — rat, pedaler og briller bygges færdige | Gigabitterne |
| 13 | **Grand Prix** | Begge |

## Fast metode gennem hele forløbet

- **Arduino IDE** med **esp32 by Espressif Systems** (version 3.x). Alt foregår i C++, i små bidder: hver session bygger én del af den færdige kode i [byggevejledningen](../byggevejledning/index.md).
- **To boards pr. gruppe:** et ESP32-S3 med kamera til bilen og et ESP32-S3 DevKitC-1 til konsollen.
- **Test på bordet først:** alt testes med bilen løftet op (hjulene i luften), før den sættes på gulvet.
- **Lodning** kun med en voksen ved siden af.
