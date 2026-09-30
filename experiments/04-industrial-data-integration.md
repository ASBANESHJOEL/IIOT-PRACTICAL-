# Experiment 4: Industrial Data Integration

## Aim
Collect readings from different sensors and integrate them into one monitoring program.

## Components discussed
- LDR (light-dependent resistor)
- MQ-135 air-quality/gas sensor module
- HC-SR04 ultrasonic distance sensor
- Microcontroller

## Working principle
Each sensor measures a different physical/environmental quantity. The controller reads the sensor outputs, converts them into usable values, and combines them for monitoring.

## Procedure outline
1. Connect each sensor using its module-specific wiring.
2. Read the LDR through an analog input and interpret the relative light level.
3. Read the MQ-135 output after its required warm-up and calibration considerations.
4. Trigger and measure the HC-SR04 echo pulse to estimate distance.
5. Display or transmit the collected values together.

## Key points
- An LDR is typically used as part of a voltage divider.
- MQ-135 readings are not automatically a precise concentration measurement; calibration and environmental conditions matter.
- HC-SR04 distance is estimated from echo travel time and the speed of sound.
- Confirm voltage compatibility, especially for echo signals connected to 3.3 V boards.

## Viva
**What is sensor integration?** Combining data from multiple sensors in one system.
**What does LDR measure?** Relative light intensity.
**How does HC-SR04 work?** It measures the time taken for an ultrasonic pulse to return.
