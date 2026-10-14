---
entities:
- {entity: user, collects: [Email, Super user]}
- {entity: location-role, collects: [Role]}
- {entity: location, shows: [Name]}
references:
- {kind: code, role: implementation, target: web/src/admin/pages/UserNew.tsx}
---

# New user

Where a user is added with their roles at locations.
