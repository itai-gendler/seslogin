---
entities:
- {entity: period, collects: [Category, Start time, End time, Comment]}
- {entity: member, shows: [Given name, Surname]}
- {entity: category, shows: [Name]}
references:
- {kind: code, role: implementation, target: web/src/admin/pages/ActivityNew.tsx}
---

# New period

Where an admin records a period for a member.
