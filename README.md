# IIoT Lab Practical Preparation

A concise revision guide for 10 Industrial Internet of Things (IIoT) lab experiments.

> **Study note:** This is a preparation guide based on the experiment topics discussed. Match pin numbers, thresholds, library names, and exact code with your institution's lab record before the practical. Never publish real Wi-Fi passwords, API keys, or Blynk tokens.

## Experiments

1. [Solar Temperature Monitoring](experiments/01-solar-temperature-monitoring.md)
2. [Industrial Machine Monitoring](experiments/02-industrial-machine-monitoring.md)
3. [Predictive Maintenance](experiments/03-predictive-maintenance.md)
4. [Industrial Data Integration](experiments/04-industrial-data-integration.md)
5. [Energy Management](experiments/05-energy-management.md)
6. [Worker Safety](experiments/06-worker-safety.md)
7. [Industrial Automation](experiments/07-industrial-automation.md)
8. [Water Usage and Leakage Monitoring](experiments/08-water-usage-leakage.md)
9. [Equipment Performance Optimization](experiments/09-equipment-performance.md)
10. [IoT Security](experiments/10-iot-security.md)

## Quick revision

- **Sensor:** converts a physical quantity into a measurable signal.
- **Actuator:** performs an action, such as switching a relay or driving a motor.
- **ESP32/Arduino:** microcontroller platforms used to read sensors and control outputs.
- **IoT:** connects physical devices to networks and applications for monitoring/control.
- **Threshold:** a selected limit used to classify readings or trigger an action.
- **PWM:** pulse-width modulation; controls average power delivered to a load.
- **Predictive maintenance:** uses condition data to identify possible equipment problems before failure.
- **Telemetry:** measurement data transmitted from a device to another system.

## Safety and reproducibility

- Verify wiring and voltage levels before powering a circuit.
- Use suitable driver circuits; do not drive motors or high-current loads directly from GPIO pins.
- Use isolated and properly rated equipment for mains-voltage experiments.
- Treat example thresholds as illustrative unless confirmed by the lab record.
- Store credentials in local configuration, not source control.

## Viva questions

See [Important Viva Questions](viva/important-questions.md).
