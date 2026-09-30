# Experiment 9: Industrial Equipment Performance Optimization System

## Aim
Use a potentiometer to control DC motor speed and SW-420 to monitor vibration events and classify operating condition.

## Algorithm
1. Read potentiometer at A0.
2. Map ADC reading 0–1023 to PWM 0–255 and speed 0–100%.
3. Output PWM to motor driver on D9.
4. Count SW-420 HIGH events on D2 for one second, waiting for each event to end.
5. Classify count ≤5 as NORMAL, ≤15 as WARNING, otherwise CRITICAL.
6. Print speed, vibration count, status, and suggested action.

## Components Required
Arduino UNO, SW-420 module, 9V DC motor, 10 kΩ potentiometer, 2N2222 transistor, 1 kΩ resistor, 1N4007 diode, 9V battery, breadboard, jumper wires.

## Procedure
1. Connect potentiometer outer pins to 5V/GND and middle pin to A0.
2. Connect SW-420 VCC/GND/DO to 5V/GND/D2.
3. Connect D9 through 1 kΩ resistor to 2N2222 base; emitter to GND; motor between +9V and collector; place diode across motor.
4. Ensure common ground and correct diode polarity; do not power motor from Arduino pin.
5. Upload code, open Serial Monitor at 9600 baud, rotate potentiometer, and record PWM/vibration/status.

## Code
```cpp
const int potPin = A0, vibrationPin = 2, motorPin = 9;
int potValue, motorPWM, speedPercent;
unsigned long vibrationCount, startTime;

void setup() {
  Serial.begin(9600);
  pinMode(potPin, INPUT); pinMode(vibrationPin, INPUT);
  pinMode(motorPin, OUTPUT);
  Serial.println("INDUSTRIAL EQUIPMENT PERFORMANCE OPTIMIZATION");
}

void loop() {
  potValue = analogRead(potPin);
  motorPWM = map(potValue, 0, 1023, 0, 255);
  speedPercent = map(potValue, 0, 1023, 0, 100);
  analogWrite(motorPin, motorPWM);

  vibrationCount = 0;
  startTime = millis();
  while (millis() - startTime < 1000) {
    if (digitalRead(vibrationPin) == HIGH) {
      vibrationCount++;
      while (digitalRead(vibrationPin) == HIGH) delay(1);
    }
  }

  const char* status;
  if (vibrationCount <= 5) status = "NORMAL";
  else if (vibrationCount <= 15) status = "WARNING";
  else status = "CRITICAL";

  Serial.println("------------------------------");
  Serial.print("Potentiometer: "); Serial.println(potValue);
  Serial.print("Motor PWM: "); Serial.println(motorPWM);
  Serial.print("Motor Speed: "); Serial.print(speedPercent); Serial.println("%");
  Serial.print("Vibration Count: "); Serial.println(vibrationCount);
  Serial.print("Equipment Status: "); Serial.println(status);
  if (vibrationCount <= 5) Serial.println("Action: Continue operation");
  else if (vibrationCount <= 15) Serial.println("Action: Reduce motor speed");
  else Serial.println("Action: Stop and inspect");
  delay(500);
}
```

**Note:** Thresholds are the record's demonstration values. SW-420 counts events, not calibrated vibration amplitude. Use a suitable transistor driver and flyback diode.
