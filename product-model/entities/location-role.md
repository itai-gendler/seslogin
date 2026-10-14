---
domain: users
references:
- {kind: code, role: implementation, target: web/src/admin/components/LocationRolesField.tsx}
- {kind: code, role: implementation, target: api/src/graphql/auth.rs#require_location_write_access}
---

# Location role

The role a user holds at one location. A user holds at most one role per location.

## Information kept

- **Role** — Admin, who views and changes everything at the location, or Read only, who views it without changing anything
