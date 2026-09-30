# IIoT Practical — Final Viva Preparation

## A. Most Repeated IIoT Viva Questions

| Question | Answer |
|---|---|
| What is IoT? | Internet of Things. |
| What is IIoT? | Industrial Internet of Things. |
| What is Arduino UNO? | A microcontroller development board. |
| What is ESP32? | A microcontroller with Wi-Fi and Bluetooth. |
| What is a sensor? | A device that detects physical changes. |
| What is an actuator? | A device that performs an action. |
| What is GPIO? | General Purpose Input/Output. |
| What is ADC? | Analog-to-Digital Converter. |
| What is PWM? | Pulse Width Modulation. |
| What is baud rate? | The rate of symbol transmission in serial communication; commonly used to describe serial communication speed. |
| What is Serial Monitor? | A tool used to view serial data. |
| What is cloud computing? | Providing computing services over the internet. |
| What is Blynk? | An IoT monitoring and control platform. |
| What is ThingSpeak? | An IoT data visualization and cloud platform. |
| What is an interrupt? | An event-based mechanism that temporarily interrupts normal program execution. |
| What is a relay? | An electrically controlled switch. |
| What is TCP? | A reliable, connection-oriented communication protocol. |
| What is HTTP POST? | An HTTP method used to send data to a server. |
| What is encryption? | Converting readable information into protected ciphertext. |
| What is hashing? | Generating a fixed-length digest from data. |

## B. The 10 Experiments — Final Memory Sheet

| No. | Experiment | Main components / concepts | Remember |
|---:|---|---|---|
| 1 | Solar temperature monitoring | DHT22, Arduino, Python, ThingSpeak | Temperature + humidity |
| 2 | Machine monitoring | SW-420 | Vibration detection |
| 3 | Predictive maintenance | DHT11 + SW-420 | Normal / Warning / Critical |
| 4 | Data integration | LDR + MQ135 + HC-SR04 | Light + Gas + Distance |
| 5 | Energy management | ESP32 + voltage/current sensors | P = VI; threshold 500 W |
| 6 | Worker safety | MQ-2 + HC-SR04 | Gas + obstacle alerts |
| 7 | Industrial automation | 4-channel relay + motors | Active LOW |
| 8 | Water leakage | ESP32 + rain + flow sensors + Blynk | Leakage + valve control |
| 9 | Performance optimization | Potentiometer + SW-420 | PWM + vibration count |
| 10 | IoT security | PIR + AES + TCP + SHA | Secure communication |

*This is a quick-recall sheet. Follow your practical record for the exact wiring, thresholds, and code used in each experiment.*

## C. Five Code Patterns to Recognize

| Code pattern | Purpose |
|---|---|
| `pinMode(pin, OUTPUT)` | Configure a pin as an output. |
| `digitalWrite(pin, HIGH)` | Set a digital output HIGH. |
| `digitalRead(pin)` | Read a digital sensor/input. |
| `analogRead(pin)` | Read an analog input. |
| `delay(1000)` | Pause for 1 second. |

### Additional Important Functions

- `millis()` → returns elapsed milliseconds since the program started.
- `map()` → converts a value from one range to another.
- `analogWrite()` → produces a PWM output on supported pins.
- `pulseIn()` → measures the duration of a pulse.
- `attachInterrupt()` → configures an interrupt to respond to an event.
- `Blynk.virtualWrite()` → sends a value to a Blynk virtual pin.
