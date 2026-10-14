---
appliesTo:
- {type: entity, id: user, effect: changes, facts: [Email, Super user, Developer, Enabled]}
permits:
- actors:
  - super-user
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#update_user}
---

# Only a super user changes a user's email, super user, developer and enabled settings

These decide who can sign in and with what powers.
