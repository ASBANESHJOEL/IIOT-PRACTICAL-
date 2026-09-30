# Experiment 1: Solar Temperature Monitoring

## Aim
Measure temperature in a solar-related setup and make the readings available for monitoring.

## Components discussed
- Arduino or compatible microcontroller
- DHT22 temperature/humidity sensor
- Computer running Python
- ThingSpeak or another IoT dashboard

## Working principle
The DHT22 senses temperature (and humidity). The microcontroller reads the sensor and passes the measurement to a computer or network service. A dashboard such as ThingSpeak can display readings over time.

## Procedure outline
1. Connect the DHT22 data, power, and ground pins according to the module and board documentation.
2. Install the required sensor library and verify that readings are valid.
3. Read temperature periodically.
4. Send readings to the configured IoT service using its supported API.
5. Plot or inspect the measurements over time.

## Key points
- Check the sensor's supported voltage and wiring.
- A dashboard update depends on network connectivity and service limits.
- Keep API keys private; use placeholders in public examples.

## Viva
**Why use DHT22?** It provides digital temperature and humidity measurements.
**What is ThingSpeak?** An IoT platform used to collect, visualize, and analyze device data.
**Why monitor over time?** Trends can reveal changing operating conditions.
