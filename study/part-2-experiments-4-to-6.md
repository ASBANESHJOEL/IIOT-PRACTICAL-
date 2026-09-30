# Part 2 — Simple IIoT Study Notes (Experiments 4–6)

## Experiment 4: Industrial Data Integration
**Aim:** Collect readings from different sensors in one monitoring program.

**Components:** LDR, MQ-135, HC-SR04, microcontroller.

**Working:** The sensors measure different quantities. The controller reads and combines their outputs.

**Procedure:**
1. Connect each sensor according to its module wiring.
2. Read the LDR through an analog input.
3. Read MQ-135 after considering warm-up/calibration.
4. Use the HC-SR04 echo time to estimate distance.
5. Display or transmit the readings together.

**Remember:** LDR measures relative light; MQ-135 is not automatically a precise gas-concentration instrument; HC-SR04 estimates distance from ultrasonic echo time.

## Experiment 5: Energy Management
**Aim:** Monitor electrical measurements and estimate power/energy consumption.

**Components:** ESP32, voltage and current sensing modules, display or monitoring application.

**Working:** The ESP32 reads voltage and current, calculates power, and accumulates energy over time.

**Formula:** DC power, P = V × I. Energy = power × time.

**Procedure:**
1. Connect sensing modules according to their datasheets and lab circuit.
2. Read and calibrate voltage/current.
3. Calculate power.
4. Accumulate energy using the sampling interval.
5. Display or transmit results.

**Safety:** Never connect mains voltage directly to a microcontroller circuit. Use properly rated isolated measurement hardware and follow lab supervision.

## Experiment 6: Worker Safety Monitoring
**Aim:** Demonstrate gas/smoke and obstacle sensing with alerts.

**Components:** MQ-2, HC-SR04, LEDs, buzzer, microcontroller.

**Working:** MQ-2 responds to certain combustible gases/smoke. HC-SR04 estimates nearby object distance. The controller compares readings with lab limits and activates alerts.

**Procedure:**
1. Connect sensors and indicators as specified.
2. Allow the gas sensor its required warm-up.
3. Read gas output and distance.
4. Compare with lab-defined limits.
5. Activate the appropriate alert.

**Remember:** MQ-2 is not a certified life-safety detector; this prototype does not replace certified alarms.

[Experiment 4](../experiments/04-industrial-data-integration.md) · [Experiment 5](../experiments/05-energy-management.md) · [Experiment 6](../experiments/06-worker-safety.md)
