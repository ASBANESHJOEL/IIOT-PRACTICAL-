# Experiment 3: Predictive Maintenance

## Aim
Use condition readings to classify equipment state and alert when readings indicate abnormal conditions.

## Components discussed
- DHT11 temperature/humidity sensor
- SW-420 vibration sensor
- Microcontroller
- LED/buzzer alert

## Working principle
Temperature and vibration are monitored together. The program compares readings or sensor states with configured limits and assigns a state such as normal, warning, or critical.

## Procedure outline
1. Read temperature and vibration state.
2. Define limits based on the lab specification or experimental calibration.
3. Classify the current condition.
4. Display or signal the state using LEDs/buzzer.
5. Test normal and abnormal scenarios.

## Example logic (illustrative only)
- Normal: readings remain within the configured range.
- Warning: a reading approaches or crosses a warning limit.
- Critical: a severe condition is detected.

Do not treat any generic numeric threshold as a validated industrial limit.

## Key points
- Predictive maintenance aims to anticipate faults from condition data.
- A simple threshold demonstration is condition monitoring, not a complete predictive model.
- DHT11 has lower measurement precision/range than many industrial temperature sensors.

## Viva
**What is predictive maintenance?** Maintenance planned using condition information to anticipate failures.
**Why combine sensors?** Multiple signals can provide more context than one signal alone.
**What is a threshold?** A decision boundary used to trigger a classification or action.
