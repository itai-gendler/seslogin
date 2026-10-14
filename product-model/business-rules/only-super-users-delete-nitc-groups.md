---
appliesTo:
- {type: entity, id: nitc-group, effect: removes}
permits:
- actors:
  - super-user
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#delete_nitc_group}
---

# Only a super user deletes an NITC group

NITC groups decide how every location's training reaches SES.
