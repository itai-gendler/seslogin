---
entities:
- {entity: kiosk, shows: [Device key], collects: [Setup code]}
references:
- {kind: code, role: implementation, target: web/src/kiosk/components/KioskSetupForm.tsx}
- {kind: code, role: implementation, target: web/src/kiosk/components/KioskEnrollment.tsx}
---

# Setup this kiosk

Where a computer is set up as a kiosk, by entering a setup code or by showing a QR code a user scans with their phone.
