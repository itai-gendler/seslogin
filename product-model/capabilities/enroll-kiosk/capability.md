---
availability:
- {place: 'dashboard::location-dashboard'}
domain: kiosks
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#enroll_session}
---

# Enroll a kiosk by QR code

A computer waiting to become a kiosk shows a QR code; a user scans it with their phone, chooses the location and a name, and the computer starts working as that kiosk without a code. Enrolling a computer that was already a kiosk moves it onto the new entry.
