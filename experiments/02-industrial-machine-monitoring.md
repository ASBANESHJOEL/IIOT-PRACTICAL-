# Experiment 2: Industrial Machine Monitoring

## Aim
Detect vibration from a machine or model setup and provide a local alert.

## Components discussed
- SW-420 vibration sensor module
- Microcontroller
- LED and buzzer

## Working principle
The vibration module changes its digital output when vibration crosses its internal sensitivity setting. The controller reads the output and activates an LED or buzzer when vibration is detected.

## Procedure outline
1. Connect the module output to a suitable digital input.
2. Connect the LED and buzzer through appropriate driver/current-limiting components.
3. Read the sensor state repeatedly.
4. Turn on the alert output when vibration is detected; otherwise keep it inactive.
5. Test with gentle, controlled vibration.

## Key points
- SW-420 modules commonly provide a threshold-style digital output; they do not provide calibrated vibration magnitude.
- Adjust sensitivity carefully and avoid loose wiring.
- For real machinery, use appropriate industrial-grade sensing and safety procedures.

## Viva
**What does SW-420 detect?** Vibration or shock events above its set sensitivity.
**Why use a buzzer?** To provide an audible local warning.
**Is this a vibration spectrum analyzer?** No; a basic SW-420 module is generally a threshold detector.
