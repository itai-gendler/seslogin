---
actors:
- member
- guest
access: authenticated
references:
- {kind: code, role: implementation, target: web/src/kiosk/components/KioskSessionProvider.tsx}
---

# Enrolled kiosk

A kiosk set up for one location, used by whoever walks up to it: members signing in and out, and guests where the kiosk offers them.
