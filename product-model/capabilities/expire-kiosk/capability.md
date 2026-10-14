---
availability:
- {place: 'dashboard::location-dashboard'}
domain: kiosks
references:
- {kind: code, role: implementation, target: api/src/session_key.rs}
- {kind: doc, role: intent, target: MANUAL.md}
---

# Expire an idle kiosk

A kiosk set up by QR code that makes no contact for two weeks expires and stops working.
