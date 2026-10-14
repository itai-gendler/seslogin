---
availability:
- {place: 'dashboard::location-dashboard'}
domain: kiosks
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#reactivate_session}
---

# Reactivate a kiosk

An admin brings back a kiosk set up by QR code that expired, keeping its name and settings, while the computer is switched on and showing its QR code.
