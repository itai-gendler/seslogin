---
entities:
- {entity: member, shows: [Given name, Surname]}
- {entity: category, shows: [Name]}
- {entity: period, shows: [Start time, End time]}
references:
- {kind: code, role: implementation, target: web/src/admin/pages/ActivityDailyBreakdown.tsx}
---

# Daily breakdown

Each day's time per category and member over a chosen range.
