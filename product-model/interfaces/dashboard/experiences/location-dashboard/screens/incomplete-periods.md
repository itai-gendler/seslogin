---
entities:
- {entity: period, shows: [Start time, Category, Signed in at]}
- {entity: guest-period, shows: [Guest name, Start time]}
- {entity: member, shows: [Given name, Surname, Home unit]}
- {entity: category, shows: [Name]}
references:
- {kind: code, role: implementation, target: web/src/admin/pages/ActivityCurrent.tsx}
---

# Incomplete periods

Members and guests currently signed in at the location.
