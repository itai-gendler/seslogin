---
availability:
- {place: 'dashboard::location-dashboard'}
domain: members
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#delete_person}
---

# Delete a member

An admin removes a member who was added by hand from the roster.
