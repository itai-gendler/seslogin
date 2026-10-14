---
availability:
- {place: 'dashboard::administration'}
domain: users
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#create_user}
---

# Add a user

A super user gives someone access to the dashboard, with a role at each of their locations.
