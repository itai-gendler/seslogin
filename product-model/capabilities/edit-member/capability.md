---
availability:
- {place: 'dashboard::location-dashboard'}
domain: members
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#update_person}
---

# Edit a member

An admin changes the name or member ID of a member who was added by hand.
