# Part 3 — Simple IIoT Study Notes (Experiments 7–10)

## Experiment 7: Industrial Automation
**Aim:** Control electrical loads using a relay module and microcontroller.

**Components:** Microcontroller, 4-channel relay module, motors or demonstration loads.

**Working:** Controller outputs switch relay channels. Check whether the specific board is active HIGH or active LOW.

**Procedure:**
1. Identify relay supply, input, and contact terminals.
2. Connect controller outputs to relay inputs.
3. Use suitable low-voltage demonstration loads unless properly supervised.
4. Run a switching sequence.
5. Verify relay logic.

**Remember:** GPIO pins cannot power motors directly. Use suitable drivers and rated supplies. Never handle exposed mains wiring.

## Experiment 8: Water Usage and Leakage Monitoring
**Aim:** Monitor water-related readings and demonstrate remote status/control.

**Components:** ESP32, rain/water detection sensor, flow sensor, Blynk, relay/valve as specified.

**Working:** Water detection indicates water presence. A flow sensor generates pulses related to flow. ESP32 sends data to Blynk; a relay may control a suitable valve.

**Procedure:**
1. Connect sensors and relay according to the lab circuit.
2. Count flow pulses over a known interval.
3. Convert pulse frequency using the sensor's calibration factor.
4. Detect water presence or unexpected flow using the lab logic.
5. Send status to Blynk and test control.

**Remember:** Flow conversion depends on the exact sensor and calibration. Keep electronics protected from water; do not publish Blynk tokens.

## Experiment 9: Equipment Performance Optimization
**Aim:** Demonstrate motor control and observe response using sensor feedback.

**Components:** Potentiometer, SW-420, PWM-capable microcontroller output, DC motor and suitable driver.

**Working:** Potentiometer provides an analog input. The controller maps it to PWM duty cycle to vary motor speed. SW-420 gives a basic vibration indication.

**Procedure:**
1. Read the potentiometer.
2. Map the value to a PWM range.
3. Drive the motor through a suitable driver.
4. Read vibration state.
5. Compare settings and observed behavior.

**Remember:** PWM varies average output by changing duty cycle. SW-420 is not a calibrated vibration instrument. Changing speed alone does not prove efficiency improvement.

## Experiment 10: IoT Security
**Aim:** Demonstrate protected communication and integrity checking.

**Components/concepts:** ESP32, PIR, AES-256-GCM, TCP, Python receiver, SHA-256.

**Working:** ESP32 reads the PIR and sends event data to a receiver. AES-GCM can provide confidentiality and authentication when correctly implemented. SHA-256 creates a digest; a plain hash alone does not authenticate the sender.

**Procedure:**
1. Read PIR state.
2. Prepare event payload.
3. Encrypt/authenticate using AES-GCM.
4. Send data over TCP.
5. Receiver authenticates and decrypts before use.
6. Perform the SHA-256 comparison if required by the lab.

**Remember:** TCP is not encryption. SHA-256 is hashing, not encryption. AES-GCM requires a unique nonce for each encryption with the same key. Never publish real keys or credentials.

[Experiment 7](../experiments/07-industrial-automation.md) · [Experiment 8](../experiments/08-water-usage-leakage.md) · [Experiment 9](../experiments/09-equipment-performance.md) · [Experiment 10](../experiments/10-iot-security.md)
