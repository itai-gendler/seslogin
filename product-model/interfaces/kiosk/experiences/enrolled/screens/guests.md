---
entities:
- {entity: guest-period, shows: [Guest name, Start time], collects: [Guest name, Comment]}
references:
- {kind: code, role: implementation, target: web/src/kiosk/components/ScanGuestDialog.tsx}
---

# Guest sign in / out

Where a guest is signed in by name and where guests currently signed in are listed to be signed out.
