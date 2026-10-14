---
appliesTo:
- {type: entity, id: audit-log-entry, effect: reads, facts: [IP address]}
permits:
- actors:
  - super-user
references:
- {kind: code, role: implementation, target: api/src/graphql/audit_log.rs}
---

# Only super users see the IP address a change came from

An IP address is personal data.
