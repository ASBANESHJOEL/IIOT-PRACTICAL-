# Experiment 8: Water Usage and Leakage Monitoring

## Aim
Monitor water-related sensor readings and demonstrate remote status/control.

## Components discussed
- ESP32
- Rain/water detection sensor
- Water flow sensor
- Blynk IoT platform
- Relay/valve (as described in the experiment topic)

## Working principle
A water detection sensor indicates the presence of water on its sensing surface. A flow sensor generates pulses related to water flow. The ESP32 reads these signals and can send data to a Blynk dashboard; a relay may control a suitable valve in the demonstration.

## Procedure outline
1. Connect sensors and relay according to their datasheets and lab circuit.
2. Count flow-sensor pulses over a known time interval.
3. Convert pulse frequency to flow rate using the sensor's calibration factor.
4. Detect water presence or unexpected flow according to the lab's logic.
5. Send status to Blynk and test the control output.

## Key points
- Flow conversion depends on the exact sensor model and calibration.
- Keep electronics protected from water.
- Store Blynk credentials securely; never commit real tokens.

## Viva
**What does a flow sensor measure?** The movement/rate of fluid through a pipe.
**Why count pulses?** Pulse frequency is related to flow for the selected sensor.
**What is Blynk?** An IoT platform for device connectivity and dashboards.
