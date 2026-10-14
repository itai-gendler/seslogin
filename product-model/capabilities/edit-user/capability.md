---
availability:
- {place: 'dashboard::administration'}
domain: users
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#update_user}
---

# Edit a user

A super user changes a user's email address, whether they are a super user or a developer, and whether they can sign in.
