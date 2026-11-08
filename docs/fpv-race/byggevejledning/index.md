# BYGGEVEJLEDNING

Den samlede tekniske vejledning til FPV Car Race: indkøbsliste, ledningsføring og koden til bil og konsol. Siden er primært til **underviserne** — de enkelte sessioner henviser hertil og tager det i små bidder.

!!! warning "Koden er ikke testet på rigtig hardware endnu"
    Koden herunder er skrevet ud fra den oprindelige projektbeskrivelse, rettet for de fejl, der er beskrevet i "Ændringer i forhold til den oprindelige vejledning", men den er **ikke afprøvet på de fysiske boards endnu**. Byg og test den inden forløbet starter, og ret denne side til, hvis noget skal justeres.

## Ændringer i forhold til den oprindelige vejledning

Vejledningen bygger på en tidligere beskrivelse af projektet. Den er rettet på disse punkter:

| Hvad | Oprindeligt | Nu | Hvorfor |
|---|---|---|---|
| Video | Ingen kode | Bilen sender JPEG-billeder over WiFi, konsollen viser dem på begge skærme | Videodelen manglede helt |
| Radio | ESP-NOW til styring | WiFi til både styring (UDP) og video (TCP) | Når videoen alligevel kører over WiFi, er én forbindelse enklere end to. Ingen MAC-adresser at finde, og hver bil har sit eget netnavn, så flere biler kan køre samtidig uden at forstyrre hinanden |
| Motor IN2 | GPIO 4 | GPIO 14 | GPIO 4 bruges af kameraet på kamera-boardet |
| Nødstop | Intet | Motor stopper efter 0,5 s uden signal | Ellers kører bilen videre med sidste fart, hvis forbindelsen ryger |
| Motordriver | L9110S eller TB6612FNG | L9110S | Ledningsføringen passer kun til L9110S (TB6612FNG kræver flere ben) |
| Motorfart | 0-255 direkte på batteriet | Loft (`MAX_FART`) | Små gule TT-motorer er lavet til 3-6 V, batteriet giver 7,4 V |

## Indkøbsliste

Pr. bil + konsol (ét sæt pr. gruppe).

### Til bilen

| Antal | Del | Bemærkning |
|---|---|---|
| 1 | ESP32-S3 med kamera, fx **Freenove ESP32-S3 WROOM CAM** (OV2640, 8 MB PSRAM) | Med USB-C. Pinnene i koden passer til Freenove-boardet — tjek pinout, hvis I køber et andet |
| 1 | Bil-chassis med baghjulstræk (DC-motor) og forhjulsstyring med **SG90/MG90S-servo** | |
| 1 | Motordriver **L9110S** | |
| 1 | Batteriholder til 2x 18650 + 2 **beskyttede** 18650 Li-ion-celler + lader | 7,4 V |
| 1 | 5V buck converter (step-down), mindst 2 A | Strøm til ESP32 og servo |
| 1 | Lille vippekontakt | Tænd/sluk mellem batteri og resten |

### Til konsollen (rat, pedaler og briller)

| Antal | Del | Bemærkning |
|---|---|---|
| 1 | **ESP32-S3 DevKitC-1** (helst N8R8-udgaven med PSRAM) | Med USB-C, uden kamera |
| 2 | **ST7789 SPI-skærm 240x240**, 1,3-1,54" | Helst samme model begge to |
| 3 | Potentiometer 10 kΩ (drejepotentiometer) | Rat, speeder, bremse |
| 1 | VR-brille til smartphone (fx VR Box) | Telefonholderen pilles ud, skærmene limes ind |
| 1 | Powerbank med USB-C | |

### Værktøj og diverse

Jumperledninger (Dupont), loddekolbe og loddetin, limpistol, skydelære, pap/træ/3D-print til rattet og pedalerne, et par små fjedre til pedalerne.

## Ledningsføring: bilen

| Fra | Til |
|---|---|
| Servo brun (GND) | Fælles GND |
| Servo rød (+) | 5V fra buck converter |
| Servo orange (signal) | **GPIO 1** |
| L9110S VCC | Batteri + (efter kontakten) |
| L9110S GND | Fælles GND |
| L9110S A-IA (frem) | **GPIO 2** |
| L9110S A-IB (bak) | **GPIO 14** |
| L9110S motorudgang A | DC-motoren |
| Batteri + (efter kontakten) | Buck converter IN+ |
| Batteri - | Buck converter IN- og fælles GND |
| Buck converter OUT+ (5V) | ESP32 **5V**-ben og servo rød |
| Buck converter OUT- | Fælles GND |

!!! warning "Indstil buck converteren før den sættes til"
    Mange buck convertere har en lille skrue, der bestemmer udgangsspændingen. Mål med et multimeter, at den giver **5,0 V**, *før* ESP32 og servo sættes på. Og: tag batteriet fra (sluk kontakten), når bilen er sat til computeren med USB.

## Ledningsføring: konsollen

**Potentiometre** (alle tre ens): venstre ben til **3.3V**, højre ben til **GND**, midterste ben:

| Potentiometer | Midterste ben til |
|---|---|
| Rat | **GPIO 4** |
| Speeder | **GPIO 5** |
| Bremse | **GPIO 6** |

**De to skærme** forbindes *parallelt*: samme ben på begge skærme samles og føres til ét ben på ESP32. Så viser de præcis det samme billede, ét til hvert øje.

| Skærm-ben | ESP32-S3 |
|---|---|
| GND | GND |
| VCC | 3.3V |
| SCL (clock) | **GPIO 12** |
| SDA (data) | **GPIO 11** |
| RES (reset) | **GPIO 10** |
| DC | **GPIO 9** |
| CS | **GPIO 8** (mange 240x240-skærme har intet CS-ben — så springes det over) |
| BLK (baggrundslys, hvis det findes) | 3.3V |

## Software

1. Installer **Arduino IDE 2** fra [arduino.cc](https://www.arduino.cc/en/software).
2. **Boards Manager** → søg efter `esp32` → installer **esp32 by Espressif Systems** (version 3.x).
3. **Library Manager** → installer **ESP32Servo** (Kevin Harrington), **TFT_eSPI** (Bodmer) og **TJpg_Decoder** (Bodmer).
4. Ved upload: vælg board **ESP32S3 Dev Module**. På bilen (Freenove-boardet) skal **Tools → PSRAM** stå på **OPI PSRAM**, ellers starter kameraet ikke.

### TFT_eSPI-opsætning (kun konsollen)

TFT_eSPI læser sine indstillinger fra filen `User_Setup.h` i bibliotekets egen mappe (`Arduino/libraries/TFT_eSPI/`). Erstat indholdet med:

```cpp
#define ST7789_DRIVER
#define TFT_WIDTH  240
#define TFT_HEIGHT 240

#define TFT_MOSI 11
#define TFT_SCLK 12
#define TFT_CS    8   // skriv -1, hvis skærmene ikke har et CS-ben
#define TFT_DC    9
#define TFT_RST  10

#define USE_HSPI_PORT   // nødvendig på ESP32-S3, ellers kan den gå ned ved opstart

#define LOAD_GLCD
#define LOAD_FONT2
#define LOAD_FONT4

#define SPI_FREQUENCY 40000000   // sæt ned til 27000000, hvis billedet flimrer
```

Filen overskrives, når biblioteket opdateres, så gem en kopi.

## Kode 1: Bilen

Uploades til kamera-boardet. Bilen laver sit eget WiFi-net, lytter efter styrepakker og sender kamerabilleder til konsollen.

```cpp
// FPV Car Race - BILEN
// Board: ESP32S3 Dev Module, PSRAM: OPI PSRAM
// Kamera-board: Freenove ESP32-S3 WROOM CAM

#include <WiFi.h>
#include <WiFiUdp.h>
#include <ESP32Servo.h>
#include "esp_camera.h"

// ---- Hver bil sine egne indstillinger ----
const char* BIL_NAVN = "CPR-BIL-1";   // bil 2: CPR-BIL-2 osv.
const char* KODEORD  = "piratbil1";   // mindst 8 tegn
const int   KANAL    = 1;             // bil 1: 1, bil 2: 6, bil 3: 11

// ---- Pins ----
#define SERVO_PIN  1
#define MOTOR_IN1  2    // frem
#define MOTOR_IN2  14   // bak (IKKE GPIO 4 - den bruger kameraet)

const int MAX_FART  = 180;  // loft over motorkraften (0-255)
const int NODSTOP_MS = 500; // stop motoren efter så lang tid uden signal

const int STYR_PORT  = 4210;  // styrepakker kommer ind her (UDP)
const int VIDEO_PORT = 81;    // konsollen henter video her (TCP)

// ---- Kamera-pins til Freenove ESP32-S3 WROOM CAM ----
#define PWDN_GPIO_NUM  -1
#define RESET_GPIO_NUM -1
#define XCLK_GPIO_NUM  15
#define SIOD_GPIO_NUM   4
#define SIOC_GPIO_NUM   5
#define Y9_GPIO_NUM    16
#define Y8_GPIO_NUM    17
#define Y7_GPIO_NUM    18
#define Y6_GPIO_NUM    12
#define Y5_GPIO_NUM    10
#define Y4_GPIO_NUM     8
#define Y3_GPIO_NUM     9
#define Y2_GPIO_NUM    11
#define VSYNC_GPIO_NUM  6
#define HREF_GPIO_NUM   7
#define PCLK_GPIO_NUM  13

// Datapakken fra rattet (skal være PRÆCIS som på konsollen!)
typedef struct {
  int servoVinkel;
  int motorFart;
  int retning;   // 0 = stop, 1 = frem, 2 = bak
} Styring;

Styring styring;
Servo forhjulServo;
WiFiUDP udp;
WiFiServer videoServer(VIDEO_PORT);
WiFiClient videoKlient;
unsigned long sidsteBesked = 0;

void stopMotor() {
  analogWrite(MOTOR_IN1, 0);
  analogWrite(MOTOR_IN2, 0);
}

void korBil() {
  forhjulServo.write(styring.servoVinkel);

  int fart = constrain(styring.motorFart, 0, MAX_FART);
  if (styring.retning == 1) {        // FREM
    analogWrite(MOTOR_IN1, fart);
    analogWrite(MOTOR_IN2, 0);
  } else if (styring.retning == 2) { // BAK
    analogWrite(MOTOR_IN1, 0);
    analogWrite(MOTOR_IN2, fart);
  } else {                           // STOP
    stopMotor();
  }
}

// Læs alle styrepakker, der er kommet siden sidst
void modtagStyring() {
  while (udp.parsePacket() == sizeof(Styring)) {
    udp.read((uint8_t*)&styring, sizeof(Styring));
    sidsteBesked = millis();
    korBil();
  }
}

// Nødstop: ingen besked i et stykke tid = stop motoren
void tjekNodstop() {
  if (millis() - sidsteBesked > NODSTOP_MS) {
    stopMotor();
  }
}

bool startKamera() {
  camera_config_t config = {};
  config.ledc_channel = LEDC_CHANNEL_0;
  config.ledc_timer   = LEDC_TIMER_0;
  config.pin_d0 = Y2_GPIO_NUM;  config.pin_d1 = Y3_GPIO_NUM;
  config.pin_d2 = Y4_GPIO_NUM;  config.pin_d3 = Y5_GPIO_NUM;
  config.pin_d4 = Y6_GPIO_NUM;  config.pin_d5 = Y7_GPIO_NUM;
  config.pin_d6 = Y8_GPIO_NUM;  config.pin_d7 = Y9_GPIO_NUM;
  config.pin_xclk  = XCLK_GPIO_NUM;
  config.pin_pclk  = PCLK_GPIO_NUM;
  config.pin_vsync = VSYNC_GPIO_NUM;
  config.pin_href  = HREF_GPIO_NUM;
  config.pin_sccb_sda = SIOD_GPIO_NUM;
  config.pin_sccb_scl = SIOC_GPIO_NUM;
  config.pin_pwdn  = PWDN_GPIO_NUM;
  config.pin_reset = RESET_GPIO_NUM;
  config.xclk_freq_hz = 20000000;
  config.pixel_format = PIXFORMAT_JPEG;
  config.frame_size   = FRAMESIZE_240X240;  // samme størrelse som skærmene
  config.jpeg_quality = 12;                 // lavere tal = pænere, men større billeder
  config.fb_count     = 2;
  config.fb_location  = CAMERA_FB_IN_PSRAM;
  config.grab_mode    = CAMERA_GRAB_LATEST; // send altid det nyeste billede
  return esp_camera_init(&config) == ESP_OK;
}

// Send ét billede: først størrelsen (4 bytes), så selve billedet
void sendBillede() {
  camera_fb_t* fb = esp_camera_fb_get();
  if (!fb) return;
  uint32_t laengde = fb->len;
  videoKlient.write((uint8_t*)&laengde, 4);
  videoKlient.write(fb->buf, fb->len);
  esp_camera_fb_return(fb);
}

void setup() {
  Serial.begin(115200);

  pinMode(MOTOR_IN1, OUTPUT);
  pinMode(MOTOR_IN2, OUTPUT);
  stopMotor();

  forhjulServo.attach(SERVO_PIN);
  forhjulServo.write(90);  // ligeud

  if (!startKamera()) {
    Serial.println("Kameraet kunne ikke starte - tjek PSRAM-indstillingen");
  }

  WiFi.softAP(BIL_NAVN, KODEORD, KANAL);
  Serial.print("Bilen er klar. Netnavn: ");
  Serial.println(BIL_NAVN);

  udp.begin(STYR_PORT);
  videoServer.begin();
}

void loop() {
  modtagStyring();
  tjekNodstop();

  // Ny konsol, der vil se video?
  if (!videoKlient || !videoKlient.connected()) {
    videoKlient = videoServer.accept();
  }

  if (videoKlient && videoKlient.connected()) {
    sendBillede();
  } else {
    delay(5);
  }
}
```

## Kode 2: Konsollen

Uploades til ESP32-S3 DevKitC-1 i konsollen. Den kobler sig på bilens WiFi, sender rat og pedaler og viser videoen på begge skærme.

```cpp
// FPV Car Race - KONSOLLEN (rat, pedaler og briller)
// Board: ESP32S3 Dev Module
// Kræver: TFT_eSPI (med User_Setup.h fra byggevejledningen) og TJpg_Decoder

#include <WiFi.h>
#include <WiFiUdp.h>
#include <TFT_eSPI.h>
#include <TJpg_Decoder.h>

// ---- Skal passe til DIN bil ----
const char* BIL_NAVN = "CPR-BIL-1";
const char* KODEORD  = "piratbil1";

IPAddress bilIP(192, 168, 4, 1);  // bilens adresse i sit eget WiFi-net
const int STYR_PORT  = 4210;
const int VIDEO_PORT = 81;

// ---- Pins til rat og pedaler ----
const int ratPin     = 4;
const int speederPin = 5;
const int bremsePin  = 6;

// Datapakken vi sender til bilen (skal være PRÆCIS som på bilen!)
typedef struct {
  int servoVinkel;
  int motorFart;
  int retning;   // 0 = stop, 1 = frem, 2 = bak
} Styring;

Styring minStyring;
TFT_eSPI tft;
WiFiUDP udp;
WiFiClient video;

const size_t MAX_BILLEDE = 40000;  // et 240x240-billede fylder typisk 5-15 kB
uint8_t billede[MAX_BILLEDE];

// TJpg_Decoder kalder denne funktion for hver lille blok af billedet
bool tegnBlok(int16_t x, int16_t y, uint16_t w, uint16_t h, uint16_t* bitmap) {
  if (y >= tft.height()) return false;
  tft.pushImage(x, y, w, h, bitmap);
  return true;
}

void visBesked(const char* tekst) {
  tft.fillScreen(TFT_BLACK);
  tft.setTextColor(TFT_WHITE);
  tft.drawCentreString(tekst, 120, 110, 2);
}

void sendStyring() {
  int raaRat     = analogRead(ratPin);      // 0-4095
  int raaSpeeder = analogRead(speederPin);
  int raaBremse  = analogRead(bremsePin);

  // Rat til servo-grader (venstre 60, ligeud 90, højre 120)
  minStyring.servoVinkel = map(raaRat, 0, 4095, 60, 120);

  int speederFart = map(raaSpeeder, 0, 4095, 0, 255);
  int bremseKraft = map(raaBremse, 0, 4095, 0, 255);

  if (speederFart > 15 && bremseKraft < 15) {
    minStyring.motorFart = speederFart;
    minStyring.retning = 1;  // frem
  } else if (bremseKraft > 15) {
    minStyring.motorFart = bremseKraft;
    minStyring.retning = 2;  // bak (bremsen er også bakgear)
  } else {
    minStyring.motorFart = 0;
    minStyring.retning = 0;  // stop
  }

  udp.beginPacket(bilIP, STYR_PORT);
  udp.write((uint8_t*)&minStyring, sizeof(minStyring));
  udp.endPacket();
}

void forbindTilBil() {
  visBesked("Leder efter bilen...");
  WiFi.begin(BIL_NAVN, KODEORD);
  while (WiFi.status() != WL_CONNECTED) {
    delay(200);
  }
  visBesked("Forbundet!");
}

void setup() {
  Serial.begin(115200);

  tft.init();
  tft.setRotation(0);       // prøv 1, 2 eller 3, hvis billedet vender forkert
  tft.setSwapBytes(true);   // ellers bliver farverne forkerte

  TJpgDec.setJpgScale(1);
  TJpgDec.setCallback(tegnBlok);

  WiFi.mode(WIFI_STA);
  forbindTilBil();
  udp.begin(STYR_PORT + 1);
}

void loop() {
  if (WiFi.status() != WL_CONNECTED) {
    video.stop();
    forbindTilBil();
  }

  sendStyring();

  if (!video.connected()) {
    video.connect(bilIP, VIDEO_PORT);
    delay(20);
    return;
  }

  // Hvert billede starter med 4 bytes, der fortæller hvor stort det er
  if (video.available() >= 4) {
    uint32_t laengde = 0;
    video.readBytes((uint8_t*)&laengde, 4);
    if (laengde == 0 || laengde > MAX_BILLEDE) {
      video.stop();  // noget gik galt - start forfra
      return;
    }
    if (video.readBytes(billede, laengde) == laengde) {
      TJpgDec.drawJpg(0, 0, billede, laengde);
    }
  } else {
    delay(5);
  }
}
```

## Fejlfinding

| Problem | Prøv dette |
|---|---|
| Kameraet starter ikke | **Tools → PSRAM → OPI PSRAM**. Tjek at kamerakablet sidder helt i |
| Konsollen finder ikke bilen | Er `BIL_NAVN` og `KODEORD` ens i begge programmer? Har bilen strøm? |
| Skærmene er sorte | Tjek `User_Setup.h`, især `USE_HSPI_PORT` og `TFT_CS`. Er BLK-benet forbundet? |
| Forkerte farver | `tft.setSwapBytes(true)` mangler, eller prøv uden |
| Billedet vender forkert | `tft.setRotation()` med 0-3, eller vend kameraet i koden med `sensor->set_vflip()`/`set_hmirror()` |
| Rattet styrer skævt | Skriv `raaRat` ud med `Serial.println()` og ret 0/4095 i `map()` til de tal, rattet faktisk giver |
| Bilen stopper hele tiden | Nødstoppet slår til: konsollen sender for sjældent, eller WiFi er dårligt. Kør tættere på |
| Flere biler forstyrrer hinanden | Giv hver bil sit eget `BIL_NAVN` og sin egen `KANAL` (1, 6 og 11) |

## Reference

- [Freenove ESP32-S3 WROOM CAM](https://github.com/Freenove/Freenove_ESP32_S3_WROOM_Board) — officiel dokumentation og pinout
- [ESP32-S3-DevKitC-1](https://docs.espressif.com/projects/esp-dev-kits/en/latest/esp32s3/esp32-s3-devkitc-1/index.html) — Espressifs dokumentation og pinout
- [Arduino-ESP32](https://docs.espressif.com/projects/arduino-esp32/en/latest/) — Espressifs officielle Arduino-dokumentation
- [esp32-camera](https://github.com/espressif/esp32-camera) — kamera-biblioteket
- [TFT_eSPI](https://github.com/Bodmer/TFT_eSPI) og [TJpg_Decoder](https://github.com/Bodmer/TJpg_Decoder) — skærm og JPEG-afkodning
- [ESP32Servo](https://github.com/madhephaestus/ESP32Servo) — servostyring
