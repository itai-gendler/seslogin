---
entities:
- {entity: member, shows: [Given name, Surname, Member ID, SES record, Missing from SES since]}
- {entity: location, shows: [Last successful member sync]}
references:
- {kind: code, role: implementation, target: web/src/admin/pages/MembersList.tsx}
---

# Members

The location's own members, with their sync status and the time of the last member sync.
