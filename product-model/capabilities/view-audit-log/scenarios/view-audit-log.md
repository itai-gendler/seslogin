---
kind: primary
routes:
  web: Web
steps:
- text: The User opens Audit log and chooses which kind of record to show
  kind: actor
  actor: user
  entities:
  - {entity: audit-log-entry, effect: reads, facts: [When, Who, Action, What, Changes]}
  contexts:
    web: {place: 'dashboard::location-dashboard::audit-log'}
references:
- {kind: code, role: implementation, target: api/src/graphql/audit_log.rs}
- {kind: code, role: implementation, target: web/src/admin/pages/AuditLog.tsx}
---

# Read a location's audit log

## Trigger

A user wants to know who changed something.

## Outcome

The user sees the location's changes, a member moved between units appearing in both logs.
