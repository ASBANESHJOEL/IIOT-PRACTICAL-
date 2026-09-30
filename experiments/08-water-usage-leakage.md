# Experiment 8: Smart Water Usage and Leakage Detection System in Industries

## Aim
Use ESP32, raindrop sensor, YF-S201 flow sensor, relay, LED, buzzer, solenoid valve, and Blynk to monitor flow, detect water presence/leakage, control supply, and report remotely.

## Algorithm
1. Initialize sensors, outputs, Wi-Fi, and Blynk.
2. Count flow sensor pulses using an interrupt.
3. Every second, read rain sensor and copy/reset pulse count safely.
4. Calculate flow rate = (pulses / 450) × 60 L/min (record's factor).
5. If rain sensor output is LOW, declare leakage, turn LED/buzzer ON, and activate valve relay; otherwise turn alerts OFF.
6. Send leakage status to Blynk V0 and flow rate to V1.

## Components Required
ESP32, LM393 rain sensor, YF-S201 flow sensor, 4-channel relay module, solenoid valve, 2 LEDs, buzzer, 220 Ω resistor, suitable power supplies, Wi-Fi, Blynk account/template/token, jumper wires.

## Procedure
1. Connect rain module VCC to 3V3, GND to GND, DO to D4.
2. Connect LED to D2 through 220 Ω resistor; flow sensor VCC to 5V, GND to GND, signal to D18.
3. Connect relay control pins to D26 and D27 as in the record; use a correctly rated separate supply for valve.
4. Add Blynk template details and Wi-Fi credentials locally; do not publish real tokens/passwords.
5. Upload code, connect to Wi-Fi/Blynk, and observe V0 (leak status) and V1 (flow).
6. Test with controlled water only; keep electronics dry and isolated.

## Code
```cpp
#define BLYNK_TEMPLATE_ID "YOUR_TEMPLATE_ID"
#define BLYNK_TEMPLATE_NAME "YOUR_TEMPLATE_NAME"
#define BLYNK_AUTH_TOKEN "YOUR_BLYNK_TOKEN"
#include <WiFi.h>
#include <BlynkSimpleEsp32.h>

char ssid[] = "WIFI_NAME";
char pass[] = "WIFI_PASSWORD";
const int rainSensorPin = 4, ledPin = 2, buzzerPin = 15;
const int flowSensorPin = 18, pumpRelayPin = 26, solenoidRelayPin = 27;
volatile unsigned long pulseCount = 0;
float flowRate = 0;
const float pulsesPerLiter = 450.0;
BlynkTimer timer;

void IRAM_ATTR countPulse() { pulseCount++; }

void readAndSendData() {
  int rainValue = digitalRead(rainSensorPin);
  bool leakageDetected = (rainValue == LOW);
  noInterrupts();
  unsigned long pulses = pulseCount;
  pulseCount = 0;
  interrupts();

  flowRate = (pulses / pulsesPerLiter) * 60.0;
  if (leakageDetected) {
    digitalWrite(ledPin, HIGH); digitalWrite(buzzerPin, HIGH);
    digitalWrite(solenoidRelayPin, LOW);
    Blynk.virtualWrite(V0, 1);
  } else {
    digitalWrite(ledPin, LOW); digitalWrite(buzzerPin, LOW);
    digitalWrite(solenoidRelayPin, HIGH);
    Blynk.virtualWrite(V0, 0);
  }
  Serial.print("Pulses: "); Serial.print(pulses);
  Serial.print(" | Flow rate: "); Serial.print(flowRate, 2);
  Serial.println(" L/min");
  Blynk.virtualWrite(V1, flowRate);
}

void setup() {
  Serial.begin(115200);
  pinMode(rainSensorPin, INPUT);
  pinMode(flowSensorPin, INPUT_PULLUP);
  pinMode(ledPin, OUTPUT); pinMode(buzzerPin, OUTPUT);
  pinMode(pumpRelayPin, OUTPUT); pinMode(solenoidRelayPin, OUTPUT);
  digitalWrite(ledPin, LOW); digitalWrite(buzzerPin, LOW);
  digitalWrite(pumpRelayPin, HIGH); digitalWrite(solenoidRelayPin, HIGH);
  attachInterrupt(digitalPinToInterrupt(flowSensorPin), countPulse, FALLING);
  WiFi.begin(ssid, pass);
  while (WiFi.status() != WL_CONNECTED) delay(500);
  Blynk.config(BLYNK_AUTH_TOKEN);
  Blynk.connect();
  timer.setInterval(1000L, readAndSendData);
}

void loop() { Blynk.run(); timer.run(); }
```

**Important:** Verify relay polarity and valve wiring before use. The record's sketch declares pumpRelayPin but does not actuate it. Flow calibration depends on the actual sensor and installation; 450 pulses/L is the record's example.
