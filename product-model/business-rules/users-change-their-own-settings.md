---
appliesTo:
- {type: entity, id: user, effect: changes, facts: [Daily email locations, Disaggregate virtual periods]}
permits:
- self: true
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#update_my_email_config}
---

# Only the user changes their own daily email and display settings

The daily email locations and how virtual time is shown are each user's own choice.
