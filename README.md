[README.md](https://github.com/user-attachments/files/33087465/README.md)
# Vigilance
Emergency SOS app
# Vigilance — Offline-First Emergency SOS

A Google-free, privacy-first emergency SOS application for Android. Vigilance is designed to work when nothing else does, using SMS and GPS as primary transports while providing high-security local storage and automated evidence capture.

## Key Features

### 1. Hardened SOS Dispatch
- **SMS + GPS Core**: Cascades through prioritized emergency contacts with a detailed message including an **OpenStreetMap link** and a **Geo URI** for instant navigation.
- **Delivery Tracking**: Unlike standard apps, Vigilance waits for network confirmation for every part of an SOS message to ensure it actually left the device.
- **Automatic 911 Integration**: Optionally initiates a call to emergency services (911) as the final step of the SOS cascade.

### 2. Arctic Glass UI (Cold & Dark)
- **High-Contrast Design**: Optimized for legibility in high-stress, low-light, or bright-sunlight scenarios using a deep arctic blue and slate palette.
- **Safety-First SOS Button**: A sleek, semi-transparent 2-second hold-to-fill button that prevents accidental triggers while providing clear visual and tactile feedback.
- **Minimalist Navigation**: Fast access to Contacts, Medical ID, and Check-in settings with a borderless, typography-focused layout.

### 3. Comprehensive Trigger Suite
- **Power Button Pattern**: Exactly **5 physical presses** (screen toggles) triggers an SOS. Uses a reliable dynamic receiver that responds to all screen states.
- **Shake Detection**: A threshold-based background service for hands-free activation.
- **Safety Check-in (Dead-man's Switch)**: Set a timer (15m to 8h). If you don't check in by the deadline, an SOS fires automatically. Uses `AlarmManager` to bypass Android's battery-saving Doze mode delays.
- **Voice Keyword Spotting**: Fully offline phrase detection (e.g., "Help Me") via Vosk. *Note: Requires local model installation.*
- **Fall Detection**: Accelerometer-based signal pipeline (Free-fall -> Impact -> Stillness). *Note: Currently uses a high-confidence signal placeholder.*

### 4. Automated Evidence & Black-Box Logging
- **Default-ON Evidence Capture**: Automatically records encrypted 30-second audio/video segments during an active SOS.
- **Evidence Email Service**: Automatically emails location and Medical ID summaries to recipients if internet is available. 
- **Offline Resilience**: If data is spotty, emails are queued and sent automatically by a background worker the moment signal returns.
- **Bring Your Own SMTP**: Privacy-first design allows you to use your own mail server (Fastmail, self-hosted, etc.) instead of a centralized service.

### 5. Military-Grade Security
- **SQLCipher Storage**: All contacts, medical data, and SOS logs are encrypted at rest with a random key stored in the Android Keystore.
- **Remote Wipe via SMS**: Trigger a full-device factory reset or app-data purge by sending a secret random passphrase.
- **Hardened KDF**: Uses **PBKDF2 with HMAC-SHA256 (600,000 iterations)** to protect the remote-wipe passphrase against brute-force attacks.

## Getting Started

### Installation
1.  **Debug Build**: Install `app-debug.apk` for testing.
2.  **Permissions**: Grant SMS, Location, Camera, Microphone, and Phone permissions during onboarding to ensure all safety features function.

### Configuration
1.  **Contacts**: Add at least one emergency contact to receive SMS alerts.
2.  **Medical ID**: Fill in your allergies, medications, and blood type for first responders.
3.  **Email Evidence**: Add your SMTP credentials and recipient list to enable automated email alerts.

## Project Philosophy
Vigilance is built for the individual. It contains **zero analytics, zero trackers, and zero cloud dependencies**. It treats the device owner as the sole authority and is designed as a tool of self-protection, not surveillance.

---
*Note: This application has been hardened for reliability and security. However, always test the triggers in a safe environment and ensure your SMTP settings are correct before relying on it in a real emergency.*
