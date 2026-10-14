---
entities:
- {entity: location, shows: [Name, Last successful member sync]}
- {entity: period, shows: [Start time, End time, Category]}
- {entity: kiosk, shows: [Last contact]}
references:
- {kind: code, role: implementation, target: web/src/admin/pages/AdminHome.tsx}
---

# Home

The location's quick insights: members, activity and kiosks at a glance.
