# Experiment 10: Foundational IoT Security Framework

## Aim
Demonstrate a basic security-by-design flow for an IoT device using PIR event detection, AES-256-GCM authenticated encryption, TCP transfer, and SHA-256 logging.

## Algorithm
1. ESP32 reads PIR sensor state.
2. Build an event message.
3. Encrypt/authenticate the message with AES-256-GCM using a secret key and a unique nonce.
4. Send nonce, ciphertext, and authentication tag to a Python server over TCP.
5. Server verifies/authenticates and decrypts before processing.
6. Compute SHA-256 digest for the demonstration log.

## Components Required
ESP32, PIR sensor (HW-416-B), LED and 220–330 Ω resistor, breadboard, jumper wires, USB cable, Arduino IDE with ESP32 support, Python 3, Python `cryptography` package, computer on same network.

## Procedure
1. Connect PIR OUT to GPIO18; connect LED through resistor to GPIO23 and common GND.
2. Install ESP32 board support in Arduino IDE.
3. Install Python dependency with `pip install cryptography`.
4. Generate a 32-byte AES key and configure it securely on both ends; do not commit real keys.
5. Run the Python receiver, then upload/run the ESP32 sender with the server IP and port 5000.
6. Trigger PIR and verify that the server authenticates/decrypts the event and records its digest.

## Code — Python receiver (illustrative framed protocol)
```python
# pip install cryptography
import socket, hashlib
from cryptography.hazmat.primitives.ciphers.aead import AESGCM

HOST, PORT = "0.0.0.0", 5000
KEY = bytes.fromhex("REPLACE_WITH_64_HEX_CHARACTERS_FOR_32_BYTE_KEY")

def recv_exact(conn, n):
    data = b""
    while len(data) < n:
        chunk = conn.recv(n - len(data))
        if not chunk:
            raise ConnectionError("client disconnected")
        data += chunk
    return data

with socket.socket() as server:
    server.bind((HOST, PORT))
    server.listen()
    print("Secure IoT server listening on", PORT)
    while True:
        conn, addr = server.accept()
        with conn:
            # Frame: 12-byte nonce + 2-byte ciphertext length + ciphertext+16-byte GCM tag
            nonce = recv_exact(conn, 12)
            length = int.from_bytes(recv_exact(conn, 2), "big")
            encrypted = recv_exact(conn, length)
            plaintext = AESGCM(KEY).decrypt(nonce, encrypted, None)
            digest = hashlib.sha256(plaintext).hexdigest()
            print("Authenticated event from", addr, ":", plaintext.decode())
            print("SHA256:", digest)
```

## Code — ESP32 PIR sender (requires a compatible AES-GCM library)
```cpp
// Install/use an ESP32-compatible AES-GCM library and adapt its API.
// This transport sketch shows sensor + TCP framing; encryption must be
// implemented by that library using a unique 12-byte nonce per message.
#include <WiFi.h>
const int pirPin = 18, ledPin = 23;
const char* ssid = "WIFI_NAME";
const char* password = "WIFI_PASSWORD";
const char* serverIP = "192.168.1.10";
const uint16_t serverPort = 5000;

void setup() {
  Serial.begin(115200);
  pinMode(pirPin, INPUT);
  pinMode(ledPin, OUTPUT);
  WiFi.begin(ssid, password);
  while (WiFi.status() != WL_CONNECTED) delay(500);
}

void loop() {
  bool motion = digitalRead(pirPin);
  digitalWrite(ledPin, motion ? HIGH : LOW);
  if (motion) {
    // Replace this placeholder with AES-256-GCM output:
    // nonce[12], ciphertext and 16-byte authentication tag.
    // Do not send plaintext in a system described as encrypted.
    Serial.println("Motion detected: encrypt event with AES-GCM before TCP send");
    delay(1000);
  }
  delay(100);
}
```

**Important:** This experiment requires the AES-GCM sender implementation from your official record/library to be fully executable; the ESP32 block above deliberately marks the encryption call as a placeholder rather than pretending it is complete. Use a unique nonce per encryption. TCP alone is not encryption. SHA-256 by itself does not authenticate a sender. Never publish secrets.
