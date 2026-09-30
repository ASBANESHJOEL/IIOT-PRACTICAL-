# Experiment 3: Predictive Maintenance System for Industrial Equipment

## Aim
Monitor temperature and vibration using DHT11 and SW-420 and classify equipment condition as Normal, Warning, or Critical.

## Algorithm
1. Initialize DHT11 and SW-420 inputs.
2. Read temperature and vibration state.
3. If temperature ≥45°C and vibration is detected, classify Critical.
4. Else if temperature ≥35°C or vibration is detected, classify Warning.
5. Otherwise classify Normal; display readings/status and repeat.

## Components Required
Arduino UNO, DHT11 sensor, SW-420 vibration module, breadboard, jumper wires, USB cable, 10 kΩ resistor if required by the DHT11 module, Adafruit DHT library.

## Procedure
1. Connect DHT11 DATA to D2 and SW-420 OUT to D3; connect VCC/GND correctly.
2. Install the Adafruit DHT sensor library.
3. Upload the code and open Serial Monitor at 9600 baud.
4. Observe readings under normal conditions.
5. Safely warm the sensor slightly or trigger the vibration module to demonstrate warning states. Do not expose components to unsafe heat.

## Code
```cpp
#include <DHT.h>
#define DHTPIN 2
#define DHTTYPE DHT11
const int vibrationPin = 3;
DHT dht(DHTPIN, DHTTYPE);

void setup() {
  Serial.begin(9600);
  pinMode(vibrationPin, INPUT);
  dht.begin();
}

void loop() {
  float temperature = dht.readTemperature();
  float humidity = dht.readHumidity();
  int vibration = digitalRead(vibrationPin);

  if (isnan(temperature) || isnan(humidity)) {
    Serial.println("DHT read error");
    delay(2000);
    return;
  }

  Serial.print("Temperature: "); Serial.print(temperature);
  Serial.print(" C, Humidity: "); Serial.print(humidity);
  Serial.print(" %, Vibration: "); Serial.println(vibration);

  if (temperature >= 45 && vibration == HIGH)
    Serial.println("CRITICAL: Immediate inspection required");
  else if (temperature >= 35 || vibration == HIGH)
    Serial.println("WARNING: Abnormal condition");
  else
    Serial.println("NORMAL: Equipment condition stable");

  delay(2000);
}
```

**Note:** These thresholds reproduce the classroom demonstration, not validated industrial safety limits. Confirm sensor output polarity and exact pin mapping against your record.
