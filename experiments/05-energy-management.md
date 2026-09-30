# Experiment 5: Smart Energy Management System for Industrial Plants

## Aim
Use ESP32 to monitor voltage, current, power, and energy and alert when power reaches 500 W.

## Algorithm
1. Read voltage and current sensor analog values.
2. Convert raw ADC values using the demonstration scale factors.
3. Calculate power: P = V × I.
4. Calculate elapsed time using millis() and accumulate energy in kWh.
5. If power ≥500 W, turn LED and buzzer ON; otherwise turn them OFF.
6. Print readings and status every 2 seconds.

## Components Required
ESP32, voltage sensor, current sensor, LED, buzzer, resistors, breadboard, jumper wires, USB cable, suitable low-voltage isolated test load.

## Procedure
1. Connect voltage sensor output to GPIO34 and current sensor output to GPIO35.
2. Connect LED through resistor to GPIO2 and buzzer to GPIO4; connect common ground.
3. Ensure sensor outputs stay within ESP32 ADC limits. Use only a suitable isolated low-voltage load.
4. Upload the code and open Serial Monitor at 115200 baud.
5. Test below and above the 500 W demonstration threshold; observe status and indicators.

## Code
```cpp
const int voltagePin = 34;
const int currentPin = 35;
const int ledPin = 2;
const int buzzerPin = 4;
const float powerThreshold = 500.0;
unsigned long previousMillis = 0;
float energyKWh = 0.0;

void setup() {
  Serial.begin(115200);
  pinMode(ledPin, OUTPUT);
  pinMode(buzzerPin, OUTPUT);
  digitalWrite(ledPin, LOW);
  digitalWrite(buzzerPin, LOW);
  previousMillis = millis();
  Serial.println("SMART ENERGY MANAGEMENT SYSTEM");
}

void loop() {
  int voltageRaw = analogRead(voltagePin);
  int currentRaw = analogRead(currentPin);
  float voltage = (voltageRaw / 4095.0) * 230.0;
  float current = (currentRaw / 4095.0) * 10.0;
  float power = voltage * current;

  unsigned long now = millis();
  float elapsedHours = (now - previousMillis) / 3600000.0;
  energyKWh += (power / 1000.0) * elapsedHours;
  previousMillis = now;

  bool highPower = power >= powerThreshold;
  digitalWrite(ledPin, highPower ? HIGH : LOW);
  digitalWrite(buzzerPin, highPower ? HIGH : LOW);
  Serial.println(highPower ? "STATUS: HIGH ENERGY CONSUMPTION" : "STATUS: NORMAL");
  Serial.print("Voltage: "); Serial.print(voltage, 2); Serial.println(" V");
  Serial.print("Current: "); Serial.print(current, 2); Serial.println(" A");
  Serial.print("Power: "); Serial.print(power, 2); Serial.println(" W");
  Serial.print("Energy: "); Serial.print(energyKWh, 4); Serial.println(" kWh");
  delay(2000);
}
```

**Important:** The conversion factors are the record's illustrative scaling, not universal calibration. Never connect mains directly to ESP32; use properly rated isolated sensors and qualified supervision.
