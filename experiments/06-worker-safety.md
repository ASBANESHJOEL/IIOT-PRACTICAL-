# Experiment 6: Industrial Worker Safety and Monitoring System

## Aim
Use MQ-2 and HC-SR04 with LEDs and buzzer to detect gas-level threshold and nearby obstacles and provide alerts.

## Algorithm
1. Read MQ-2 analog value.
2. Trigger HC-SR04 and measure echo duration.
3. Convert duration to distance in cm.
4. If gas value ≥300, turn gas LED ON.
5. If valid distance ≤6 cm, turn distance LED ON.
6. If either alert is active, sound buzzer; print readings/status and repeat.

## Components Required

> [!NOTE]
> Arduino UNO, MQ-2 gas sensor, HC-SR04, 2 LEDs, 2 × 220 Ω resistors, buzzer, breadboard, jumper wires, USB cable.


## Procedure
1. Connect MQ-2 VCC/GND/AO to 5V/GND/A0.
2. Connect HC-SR04 VCC/GND/TRIG/ECHO to 5V/GND/D6/D7.
3. Connect gas LED to D8 and distance LED to D9 through 220 Ω resistors; buzzer positive to D10 and negative to GND.
4. Upload code and open Serial Monitor at 9600 baud.
5. Allow MQ-2 to warm up; observe normal readings, then test the ultrasonic sensor with an object.
6. Record the readings and alerts.

## Code
```cpp
const int gasPin = A0, trigPin = 6, echoPin = 7;
const int gasLED = 8, distanceLED = 9, buzzer = 10;
const int gasThreshold = 300;
const int distanceThreshold = 6;

void setup() {
  pinMode(gasLED, OUTPUT); pinMode(distanceLED, OUTPUT);
  pinMode(buzzer, OUTPUT); pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  Serial.begin(9600);
  Serial.println("Industrial Safety Monitoring System");
}

void loop() {
  int gasValue = analogRead(gasPin);
  digitalWrite(trigPin, LOW); delayMicroseconds(2);
  digitalWrite(trigPin, HIGH); delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
  long duration = pulseIn(echoPin, HIGH, 30000);
  int distance = duration > 0 ? duration * 0.034 / 2 : -1;

  bool gasAlert = gasValue >= gasThreshold;
  bool distanceAlert = distance > 0 && distance <= distanceThreshold;
  digitalWrite(gasLED, gasAlert ? HIGH : LOW);
  digitalWrite(distanceLED, distanceAlert ? HIGH : LOW);
  digitalWrite(buzzer, (gasAlert || distanceAlert) ? HIGH : LOW);

  Serial.print("Gas Value: "); Serial.print(gasValue);
  Serial.print(" Distance: "); Serial.print(distance); Serial.println(" cm");
  if (gasAlert) Serial.println("WARNING: GAS DETECTED!");
  if (distanceAlert) Serial.println("WARNING: OBJECT TOO CLOSE!");
  Serial.println((gasAlert || distanceAlert) ? "System Status: DANGER" : "System Status: NORMAL");
  delay(1000);
}
```

**Safety note:** MQ-2 is a classroom sensor, not a certified life-safety gas detector. The 300 threshold is a demonstration value and requires calibration.
