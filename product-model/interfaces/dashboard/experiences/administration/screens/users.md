---
entities:
- {entity: user, shows: [Email, Last access, Super user]}
- {entity: location-role, shows: [Role]}
references:
- {kind: code, role: implementation, target: web/src/admin/pages/UserList.tsx}
---

# Users

Every user with their last access, super user flag and locations.
