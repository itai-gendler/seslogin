---
entities:
- {entity: member, shows: [Given name, Surname]}
- {entity: category, shows: [Name]}
- {entity: period, shows: [Start time, End time]}
references:
- {kind: code, role: implementation, target: web/src/admin/pages/ActivityBreakdown.tsx}
---

# Breakdown

Time per member by category, and per category by member, over a chosen range.
