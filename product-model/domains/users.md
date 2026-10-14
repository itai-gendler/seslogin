---
references:
- {kind: code, role: implementation, target: web/src/admin/pages/UserList.tsx}
---

# Users

The super users' Users section: who can sign in to the dashboard and their role at each location.

## Boundary

Owns users and their location roles. It does not own a user's own settings, which belong to Settings.
