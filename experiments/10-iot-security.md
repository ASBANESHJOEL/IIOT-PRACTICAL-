# Experiment 10: IoT Security

## Aim
Demonstrate protected communication and integrity checking in an IoT setup.

## Components discussed
- ESP32 with PIR motion sensor
- AES-256-GCM authenticated encryption
- TCP communication
- Python receiver
- SHA-256 hashing (as described in the experiment topic)

## Working principle
The PIR sensor detects changes associated with motion and the ESP32 sends event data to a receiver. AES-GCM can provide confidentiality and authentication when used correctly. SHA-256 produces a message digest for integrity-related demonstrations, but a plain hash alone does not authenticate the sender.

## Procedure outline
1. Read the PIR sensor state on the ESP32.
2. Prepare the event payload.
3. Encrypt/authenticate the payload using a correctly implemented AES-256-GCM library.
4. Send the resulting data over TCP to the Python receiver.
5. On the receiver, authenticate and decrypt before using the payload.
6. If the lab requires a SHA-256 demonstration, compute and compare the digest as specified.

## Security essentials
- AES-GCM requires a unique nonce for each encryption under the same key.
- Never hard-code or publish real keys, passwords, or credentials.
- TCP provides reliable byte-stream transport; it does not itself encrypt data.
- SHA-256 is a hash function, not encryption.
- Do not invent cryptographic formats; follow the exact lab code and library API.

## Viva
**What is encryption?** Transforming readable data into ciphertext using a cryptographic key.
**What does GCM provide?** Authenticated encryption: confidentiality plus integrity/authenticity.
**Does TCP secure data?** No; transport reliability is not encryption.
**Is SHA-256 reversible?** No, it is designed as a one-way hash.
