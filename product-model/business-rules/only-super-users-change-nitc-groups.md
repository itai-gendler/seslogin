---
appliesTo:
- {type: entity, id: nitc-group, effect: changes}
permits:
- actors:
  - super-user
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#update_nitc_group}
---

# Only a super user changes an NITC group

NITC groups decide how every location's training reaches SES.
