# Part 1 — Simple IIoT Study Notes (Experiments 1–3)

## Experiment 1: Solar Temperature Monitoring
**Aim:** Measure temperature in a solar-related setup and make readings available for monitoring.

**Components:** Arduino/compatible microcontroller, DHT22 temperature-humidity sensor, computer running Python, ThingSpeak or another IoT dashboard.

**Working:** DHT22 senses temperature and humidity. The controller reads the sensor and passes the measurements to a computer or network service. ThingSpeak can display readings over time.

**Procedure:**
1. Connect DHT22 power, ground, and data pins as specified for the module and board.
2. Install the sensor library and verify readings.
3. Read temperature periodically.
4. Send readings to the configured IoT service.
5. View the readings over time.

**Remember:** DHT22 provides digital temperature and humidity readings. Keep API keys private.

## Experiment 2: Industrial Machine Monitoring
**Aim:** Detect vibration and provide a local alert.

**Components:** SW-420 vibration module, microcontroller, LED, buzzer.

**Working:** The SW-420 module gives a threshold-style digital output when vibration crosses its sensitivity setting. The controller reads it and activates an LED or buzzer.

**Procedure:**
1. Connect the sensor output to a digital input.
2. Connect LED and buzzer with suitable current limiting/driver components.
3. Read the sensor repeatedly.
4. Activate the alert when vibration is detected.
5. Test using gentle, controlled vibration.

**Remember:** A basic SW-420 is not a calibrated vibration-magnitude instrument.

## Experiment 3: Predictive Maintenance
**Aim:** Use condition readings to classify equipment state and provide alerts.

**Components:** DHT11, SW-420, microcontroller, LED/buzzer.

**Working:** Temperature and vibration are monitored together. The program compares readings with configured limits and classifies the state as Normal, Warning, or Critical.

**Procedure:**
1. Read temperature and vibration.
2. Define limits from the lab specification.
3. Classify the condition.
4. Display/signal the state.
5. Test normal and abnormal cases.

**Remember:** Predictive maintenance uses condition data to anticipate failures. A simple threshold demonstration is condition monitoring, not a complete predictive model.

[Experiment 1](../experiments/01-solar-temperature-monitoring.md) · [Experiment 2](../experiments/02-industrial-machine-monitoring.md) · [Experiment 3](../experiments/03-predictive-maintenance.md)
