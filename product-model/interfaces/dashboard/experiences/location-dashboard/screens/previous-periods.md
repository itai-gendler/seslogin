---
entities:
- {entity: period, shows: [Start time, End time, Category, Comment, Signed in at, Signed out at, NITC export]}
- {entity: guest-period, shows: [Guest name, Start time, End time, Comment]}
- {entity: member, shows: [Given name, Surname, Home unit]}
- {entity: category, shows: [Name]}
references:
- {kind: code, role: implementation, target: web/src/admin/pages/ActivityList.tsx}
- {kind: code, role: implementation, target: web/src/admin/components/ActivityListTable.tsx}
---

# Previous periods

Everyone who signed in or out at the location, members visiting from other units and guests included, day by day.
