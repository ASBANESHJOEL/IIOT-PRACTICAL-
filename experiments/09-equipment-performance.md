# Experiment 9: Equipment Performance Optimization

## Aim
Demonstrate motor control and observe equipment response using input/sensor feedback.

## Components discussed
- Potentiometer
- SW-420 vibration sensor
- PWM-capable microcontroller output
- DC motor and suitable driver

## Working principle
A potentiometer provides an adjustable analog input. The controller maps this input to a PWM duty cycle to vary motor speed. A vibration sensor can provide a basic indication of vibration events.

## Procedure outline
1. Read the potentiometer using an analog input.
2. Map the reading to a valid PWM duty-cycle range.
3. Drive the motor through a suitable motor driver.
4. Read the vibration sensor and observe its response.
5. Compare operating settings and observed behavior.

## Key points
- PWM controls average delivered power by changing the duty cycle.
- Do not connect a DC motor directly to a microcontroller GPIO.
- SW-420 is a threshold detector, not a calibrated vibration measurement instrument.
- Optimization requires a defined objective and measured results; changing speed alone does not prove efficiency improvement.

## Viva
**What is PWM?** A method of controlling average output by varying pulse width.
**Why use a motor driver?** A motor needs more current than a GPIO can supply.
**What is duty cycle?** The fraction of a PWM period for which the signal is HIGH.
