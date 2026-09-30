# Experiment 1: IoT for Solar-Powered Temperature Monitoring System

## Aim
Measure temperature and humidity using DHT22 and upload the data to ThingSpeak through Arduino serial communication and a Python script.

## Algorithm
1. Initialize DHT22 on Arduino digital pin 2 and serial communication at 9600 baud.
2. Read temperature and humidity every 2 seconds.
3. Print valid readings as comma-separated values; print 0,0 on sensor error.
4. Python reads the serial line, separates temperature and humidity, and posts them to ThingSpeak fields 1 and 2.
5. Wait between cloud updates and repeat.

## Components Required
- Arduino UNO ×1
- DHT22 sensor ×1
- USB cable, jumper wires
- Laptop with internet, Arduino IDE, Python 3
- ThingSpeak channel and Write API key
- Python packages: `pyserial`, `requests`; Arduino library: `SimpleDHT`

## Procedure
1. Connect DHT22 VCC to 5V, DATA to D2, GND to GND; leave NC unconnected.
2. Connect Arduino to laptop using USB.
3. Install SimpleDHT and upload the Arduino code below.
4. Create a ThingSpeak channel with Field 1 = temp and Field 2 = hum; copy its Write API key.
5. Install Python packages with `pip install pyserial requests`.
6. Save the Python code as `upload.py`; replace COM port and API key with your own values.
7. Run `python upload.py`; verify serial readings and ThingSpeak charts.

## Code — Arduino
```cpp
#include <SimpleDHT.h>
int pinDHT22 = 2;
SimpleDHT22 dht22(pinDHT22);

void setup() { Serial.begin(9600); }

void loop() {
  byte temperature = 0, humidity = 0;
  int err = dht22.read(&temperature, &humidity, NULL);
  if (err != SimpleDHTErrSuccess) {
    Serial.println("0,0");
  } else {
    Serial.print((int)temperature);
    Serial.print(",");
    Serial.println((int)humidity);
  }
  delay(2000);
}
```

## Code — Python ThingSpeak uploader
```python
import serial
import requests
import time

API_KEY = "YOUR_WRITE_API_KEY"
PORT = "COM7"  # Change to your Arduino port
URL = "https://api.thingspeak.com/update"

ser = serial.Serial(PORT, 9600, timeout=5)
while True:
    line = ser.readline().decode(errors="ignore").strip()
    if line:
        try:
            temp, hum = line.split(",")
            if temp != "0" and hum != "0":
                response = requests.post(URL, data={
                    "api_key": API_KEY,
                    "field1": temp,
                    "field2": hum
                }, timeout=10)
                print("Uploaded:", temp, hum, "Server:", response.text)
        except (ValueError, requests.RequestException) as error:
            print("Error:", error)
    time.sleep(20)
```

**Note:** Keep the Write API key private. Change COM7 to the correct port. The Python delay respects the cloud update interval.
