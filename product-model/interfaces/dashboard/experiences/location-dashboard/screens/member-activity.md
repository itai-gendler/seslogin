---
entities:
- {entity: member, shows: [Given name, Surname]}
- {entity: period, shows: [Start time, End time, Category]}
- {entity: location, shows: [Name]}
references:
- {kind: code, role: implementation, target: web/src/admin/pages/ActivityListMember.tsx}
---

# Member activity

One member's periods at every location, newest first.
