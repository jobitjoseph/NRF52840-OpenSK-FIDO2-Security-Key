# Build Your Own FIDO2 Security Key with nRF52840 and OpenSK

An open-source USB FIDO2 security key built around the **Nordic nRF52840** and **Google's OpenSK** firmware.

This project demonstrates how to build a hardware-backed authentication device that can be used with websites and services supporting **FIDO2 / WebAuthn**.

The custom hardware uses the nRF52840's native USB interface and hardware-assisted cryptography to implement the security-key functionality. The device communicates with the host computer over USB and keeps the credential's private key on the security key rather than transferring it to the computer or website.

---

## Features

- FIDO2 / WebAuthn authentication
- nRF52840-based custom hardware
- OpenSK open-source security-key firmware
- USB HID FIDO2 transport
- Hardware-assisted cryptography using the nRF52840
- Credential private key remains on the security key
- USB DFU / UF2 firmware updates
- Custom capacitive touch input for user presence
- RGB LED for status indication
- Custom compact PCB
- Open-source hardware and firmware modifications

---

## How It Works

The security key acts as a FIDO2 authenticator between the browser and the website.

During registration, the security key generates a unique credential key pair:

```text
                 Registration

Website
   │
   │ Registration request
   ▼
Browser
   │
   │ FIDO2 / CTAP2 over USB HID
   ▼
OpenSK on nRF52840
   │
   ├── Generate credential key pair
   │
   ├── Private key ──► Stored on security key
   │
   └── Public key ───► Website
