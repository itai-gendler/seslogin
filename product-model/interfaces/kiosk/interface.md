---
type: web
actors:
- member
- guest
- user
entryPoints:
- {web: /kiosk}
references:
- {kind: code, role: implementation, target: web/src/kiosk/KioskMain.tsx}
- {kind: doc, role: intent, target: MANUAL.md}
---

# Kiosk

The part of SES Activity a unit leaves running on a computer or tablet at the unit (the "Scan" part of the site): once set up for a location, members walk up and sign in and out on it, or it shows who is signed in.
