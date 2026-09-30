# Experiment 2: Real-Time Industrial Machine Monitoring System

## Aim
Detect machine vibration using SW-420 and provide a visual and audible alert.

## Algorithm
1. Configure SW-420 output as input and LED/buzzer as outputs.
2. Read the vibration sensor.
3. If vibration is detected (HIGH in this record's wiring), turn LED and buzzer ON.
4. Otherwise turn both OFF.
5. Print status to Serial Monitor and repeat.

## Components Required

> [!NOTE]
> Arduino UNO, SW-420 vibration module, LED (with suitable resistor), active buzzer, breadboard, jumper wires, USB cable.


## Procedure
1. Connect SW-420 VCC and GND to board supply and ground; connect OUT to D2.
2. Connect LED to D13 (or the board's built-in LED) and buzzer to D8, with appropriate driver/current limiting.
3. Upload the code and open Serial Monitor at 9600 baud.
4. Apply gentle vibration and observe the sensor state and alert.
5. Adjust module sensitivity if available.

## Code
```cpp
const int vibrationPin = 2;
const int ledPin = 13;
const int buzzerPin = 8;

void setup() {
  pinMode(vibrationPin, INPUT);
  pinMode(ledPin, OUTPUT);
  pinMode(buzzerPin, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  int vibration = digitalRead(vibrationPin);
  if (vibration == HIGH) {
    digitalWrite(ledPin, HIGH);
    digitalWrite(buzzerPin, HIGH);
    Serial.println("Vibration detected!");
  } else {
    digitalWrite(ledPin, LOW);
    digitalWrite(buzzerPin, LOW);
    Serial.println("Machine normal");
  }
  delay(500);
}
```

**Note:** SW-420 is a threshold-type vibration switch, not a calibrated vibration measurement device. Confirm output polarity for the actual module.
