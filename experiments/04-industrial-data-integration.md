# Experiment 4: Industrial Data Integration and Analytics System

## Aim
Read and integrate light, air-quality/gas, and distance measurements using LDR, MQ-135, and HC-SR04.

## Algorithm
1. Initialize LDR and MQ-135 analog inputs and HC-SR04 trigger/echo pins.
2. Read LDR and MQ-135 analog values.
3. Trigger the ultrasonic sensor and measure echo duration.
4. Convert echo duration to distance in centimeters.
5. Print all readings together every 5 seconds.

## Components Required

> [!NOTE]
> Arduino UNO, LDR and voltage-divider resistor, MQ-135 module, HC-SR04 ultrasonic sensor, breadboard, jumper wires, USB cable.


## Procedure
1. Connect LDR divider output to A0 and MQ-135 analog output to A1.
2. Connect HC-SR04 TRIG to D9 and ECHO to D10; connect VCC/GND.
3. Upload the code and open Serial Monitor at 9600 baud.
4. Vary light, observe MQ-135 response after warm-up, and move an object in front of HC-SR04.
5. Record the three sensor values.

## Code
```cpp
const int ldrPin = A0;   // Explicit declaration for the record's missing variable
const int mqPin = A1;
const int trigPin = 9;
const int echoPin = 10;

void setup() {
  Serial.begin(9600);
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
}

void loop() {
  int lightValue = analogRead(ldrPin);
  int gasValue = analogRead(mqPin);

  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  long duration = pulseIn(echoPin, HIGH, 30000);
  float distance = duration > 0 ? duration * 0.0343 / 2.0 : -1;

  Serial.print("Light: "); Serial.print(lightValue);
  Serial.print(" | MQ135: "); Serial.print(gasValue);
  Serial.print(" | Distance: "); Serial.print(distance);
  Serial.println(" cm");
  delay(5000);
}
```

**Note:** The source record's code uses `ldrPin` without declaring it; this version adds `const int ldrPin = A0;` to make it compile. MQ-135 raw values are not calibrated gas concentrations. Check voltage compatibility before connecting echo to a 3.3 V board.
