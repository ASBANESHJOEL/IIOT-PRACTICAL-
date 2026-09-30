# Experiment 5: Energy Management

## Aim
Monitor electrical measurements and estimate power and energy consumption.

## Components discussed
- ESP32
- Voltage and current sensing modules
- Monitoring application/display

## Working principle
Voltage and current sensors provide measurements to the ESP32. The program calculates electrical power and accumulates energy over time.

## Core relationships
- DC power: P = V × I
- Energy: E = P × time
- For varying power, energy is estimated by accumulating power over small time intervals.

## Procedure outline
1. Connect the sensing modules according to their datasheets and the lab circuit.
2. Read and calibrate voltage/current measurements.
3. Calculate power from the measured values.
4. Accumulate energy using the sampling interval.
5. Display or transmit readings.

## Safety
Do not connect mains voltage to a microcontroller circuit directly. Use properly rated, isolated measurement hardware and follow the lab supervisor's instructions.

## Viva
**What is power?** The rate of energy transfer or use.
**What is energy consumption?** Power integrated over time.
**Why calibrate sensors?** To reduce measurement error and improve accuracy.
