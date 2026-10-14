---
entities:
- {entity: member, shows: [Given name, Surname]}
- {entity: period, shows: [Start time], collects: [Category, Start time, End time]}
- {entity: category, shows: [Name]}
references:
- {kind: code, role: implementation, target: web/src/kiosk/components/ScanController.tsx}
- {kind: code, role: implementation, target: web/src/kiosk/components/ScanScreenAdjust.tsx}
---

# Sign out

The sign-out process for one member: the forgotten-sign-out question, the quick-pick and full category choices, and the adjustable times.
