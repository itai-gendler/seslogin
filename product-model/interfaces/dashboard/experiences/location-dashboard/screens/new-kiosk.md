---
entities:
- {entity: kiosk, shows: [Setup code], collects: [Name, Mode, Guests, Quick pick categories, Who's here, Health check URL]}
- {entity: location, shows: [Name]}
references:
- {kind: code, role: implementation, target: web/src/admin/pages/SessionsNew.tsx}
- {kind: code, role: implementation, target: web/src/admin/components/SessionCreatedInterstitial.tsx}
---

# New kiosk

Where a kiosk is created with a setup code, and the code is shown once it is.
