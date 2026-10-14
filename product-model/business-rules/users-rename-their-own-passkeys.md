---
appliesTo:
- {type: entity, id: passkey, effect: changes, facts: [Name]}
permits:
- related:
  - {verb: has, entity: user}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#rename_passkey}
---

# Only the user renames their passkeys

A passkey's name is its user's to change.
