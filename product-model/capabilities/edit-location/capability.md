---
availability:
- {place: 'dashboard::administration'}
domain: locations
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#update_location}
---

# Edit a location

A super user changes a location's name, whether it is enabled, and its NITC export settings.
