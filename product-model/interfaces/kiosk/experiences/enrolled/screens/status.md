---
entities:
- {entity: member, shows: [Given name, Surname]}
- {entity: period, shows: [Start time]}
- {entity: guest-period, shows: [Guest name, Start time]}
references:
- {kind: code, role: implementation, target: web/src/kiosk/pages/Status.tsx}
- {kind: code, role: implementation, target: web/src/kiosk/components/StatusCurrentDisplay.tsx}
---

# Status

A kiosk in Status mode: a live, non-interactive list of who is signed in at the location and for how long.
