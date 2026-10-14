---
appliesTo:
- {type: entity, id: user, effect: creates}
permits:
- actors:
  - super-user
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#create_user}
---

# Only a super user adds users

Dashboard access is given by a super user; there is no self sign-up.
