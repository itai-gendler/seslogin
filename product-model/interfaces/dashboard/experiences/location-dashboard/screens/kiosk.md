---
entities:
- {entity: kiosk, shows: [Name, Mode, Guests, Quick pick categories, Who's here, Health check URL, Diagnostics], collects: [Name, Mode, Guests, Quick pick categories, Who's here, Health check URL]}
references:
- {kind: code, role: implementation, target: web/src/admin/pages/SessionsEdit.tsx}
---

# Kiosk

One kiosk's settings and its diagnostics.
