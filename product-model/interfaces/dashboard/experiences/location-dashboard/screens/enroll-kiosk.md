---
entities:
- {entity: kiosk, shows: [Device key], collects: [Name, Mode, Guests, Quick pick categories, Who's here]}
- {entity: location, shows: [Name]}
entryPoints:
- {dashboard: /enroll}
references:
- {kind: code, role: implementation, target: web/src/enroll/SessionEnroll.tsx}
---

# Enroll this kiosk

The page a user's phone opens from a kiosk's QR code, where the kiosk is given its location and name.
