---
entities:
- {entity: period, shows: [Category, Start time, End time, Comment], collects: [Category, Start time, End time, Comment]}
- {entity: guest-period, shows: [Guest name, Start time, End time, Comment], collects: [Guest name, Start time, End time, Comment]}
- {entity: category, shows: [Name]}
references:
- {kind: code, role: implementation, target: web/src/admin/pages/ActivityEdit.tsx}
---

# Period

One period or guest period, to correct.
