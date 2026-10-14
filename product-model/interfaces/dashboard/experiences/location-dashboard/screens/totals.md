---
entities:
- {entity: member, shows: [Given name, Surname]}
- {entity: category, shows: [Name, Virtual]}
- {entity: period, shows: [Start time, End time]}
references:
- {kind: code, role: implementation, target: web/src/admin/pages/ActivityTotals.tsx}
---

# Totals

Time per member and time per category over a chosen range.
