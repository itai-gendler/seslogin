---
entities:
- {entity: period, shows: [Start time, End time, Category, Comment, Signed in at, Signed out at]}
- {entity: guest-period, shows: [Guest name, Start time, End time, Comment]}
- {entity: member, shows: [Member ID, Given name, Surname]}
references:
- {kind: code, role: implementation, target: web/src/admin/pages/Reports.tsx}
---

# Reports

Where the location's periods over a chosen range are exported as a spreadsheet.
