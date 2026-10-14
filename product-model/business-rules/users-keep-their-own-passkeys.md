---
appliesTo:
- {type: entity, id: passkey, effect: creates}
permits:
- related:
  - {verb: has, entity: user}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#finish_passkey_registration}
---

# Only the user adds, renames and deletes their passkeys

A passkey belongs to the user who added it.
