# Experiment 6: Worker Safety Monitoring

## Aim
Demonstrate environmental/obstacle sensing with visual and audible alerts.

## Components discussed
- MQ-2 gas/smoke sensor
- HC-SR04 ultrasonic sensor
- LEDs and buzzer
- Microcontroller

## Working principle
The MQ-2 module responds to certain combustible gases and smoke, while the ultrasonic sensor estimates nearby object distance. The controller checks these readings and activates alerts according to configured conditions.

## Procedure outline
1. Connect sensors and output indicators using the specified circuit.
2. Allow the gas sensor the required warm-up time.
3. Read the gas sensor output and distance measurement.
4. Compare readings with lab-defined limits.
5. Activate the corresponding LED/buzzer alert.

## Key points
- MQ-2 is a broad-response sensor and is not a certified life-safety gas detector.
- Sensor warm-up, calibration, ventilation, and environmental conditions affect readings.
- An ultrasonic sensor detects distance, not a person's identity or safety status.

## Viva
**Why use two sensors?** They monitor different hazards or conditions.
**What does MQ-2 detect?** It responds to smoke and several combustible gases.
**Can this prototype replace a certified alarm?** No.
