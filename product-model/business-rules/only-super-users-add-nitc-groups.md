---
appliesTo:
- {type: entity, id: nitc-group, effect: creates}
permits:
- actors:
  - super-user
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#create_nitc_group}
---

# Only a super user adds an NITC group

NITC groups decide how every location's training reaches SES.
