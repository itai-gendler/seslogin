---
entities:
- {entity: kiosk, shows: [Name, Last contact, Setup code, Device key, Expires, Diagnostics]}
references:
- {kind: code, role: implementation, target: web/src/admin/pages/SessionsList.tsx}
---

# Kiosks

The location's kiosks with their contact, device key, version and environment.
