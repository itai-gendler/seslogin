---
appliesTo:
- {type: entity, id: passkey, effect: removes}
permits:
- related:
  - {verb: has, entity: user}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#delete_passkey}
---

# Only the user deletes their passkeys

Deleting a passkey is its user's decision.
