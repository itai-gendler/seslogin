---
entities:
- {entity: user, shows: [Email, Super user, Developer, Enabled], collects: [Email, Super user, Developer, Enabled]}
- {entity: location-role, shows: [Role], collects: [Role]}
- {entity: location, shows: [Name]}
references:
- {kind: code, role: implementation, target: web/src/admin/pages/UserEdit.tsx}
- {kind: code, role: implementation, target: web/src/admin/components/LocationRolesField.tsx}
---

# User

One user's sign-in details and their role at each location.
