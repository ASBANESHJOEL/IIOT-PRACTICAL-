# Experiment 7: Scalable Industrial Automation and Monitoring System

## Aim
Control two DC motor actuators through a 4-channel relay module using Arduino UNO, with LED status indication and serial monitoring.

## Algorithm
1. Configure relay pins D8–D11 and LEDs D6–D7 as outputs.
2. Initialize active-LOW relays to HIGH (OFF).
3. Turn Relay 1 and LED 1 ON for 4 seconds.
4. Turn them OFF for 1 second.
5. Turn Relay 2 and LED 2 ON for 4 seconds.
6. Turn them OFF for 1 second; repeat and print status.

## Components Required

> [!NOTE]
> Arduino UNO, 4-channel relay module, 2 DC motors, 2 LEDs, 2 × 220/330 Ω resistors, external DC motor supply, breadboard, wires, USB cable, computer.


## Procedure
1. Connect relay IN1–IN4 to D8–D11; VCC and GND as required by the module.
2. Connect LEDs through resistors to D6 and D7.
3. Connect motors to relay 1/2 contacts and a separate suitable motor supply.
4. Verify wiring and relay active-LOW behavior before powering.
5. Upload code and open Serial Monitor at 9600 baud.
6. Observe the repeating sequence: Motor 1 ON 4 s, OFF 1 s; Motor 2 ON 4 s, OFF 1 s.

## Code
```cpp
int relay1 = 8, relay2 = 9, relay3 = 10, relay4 = 11;
int led1 = 6, led2 = 7;

void setup() {
  pinMode(relay1, OUTPUT); pinMode(relay2, OUTPUT);
  pinMode(relay3, OUTPUT); pinMode(relay4, OUTPUT);
  pinMode(led1, OUTPUT); pinMode(led2, OUTPUT);
  digitalWrite(relay1, HIGH); digitalWrite(relay2, HIGH);
  digitalWrite(relay3, HIGH); digitalWrite(relay4, HIGH);
  digitalWrite(led1, LOW); digitalWrite(led2, LOW);
  Serial.begin(9600);
  Serial.println("Scalable Industrial Automation and Monitoring System");
}

void loop() {
  digitalWrite(relay1, LOW); digitalWrite(led1, HIGH);
  Serial.println("Motor 1 ON - LED 1 ON");
  delay(4000);
  digitalWrite(relay1, HIGH); digitalWrite(led1, LOW);
  Serial.println("Motor 1 OFF - LED 1 OFF");
  delay(1000);

  digitalWrite(relay2, LOW); digitalWrite(led2, HIGH);
  Serial.println("Motor 2 ON - LED 2 ON");
  delay(4000);
  digitalWrite(relay2, HIGH); digitalWrite(led2, LOW);
  Serial.println("Motor 2 OFF - LED 2 OFF");
  delay(1000);
}
```

**Note:** Code assumes active-LOW relay inputs. Verify your board. Use motor-rated contacts/supply; never switch exposed mains in a student setup.
