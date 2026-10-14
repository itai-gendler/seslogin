---
kind: alternative
routes:
  web: Web
steps:
- text: The Super user chooses to see changes everywhere
  kind: actor
  actor: super-user
  entities:
  - {entity: audit-log-entry, effect: reads, facts: [When, Who, Action, What, Location, Changes, IP address]}
  contexts:
    web: {place: 'dashboard::location-dashboard::audit-log'}
references:
- {kind: code, role: implementation, target: api/src/graphql/audit_log.rs}
---

# Read every location's audit log

## Trigger

A super user investigates a change across the product.

## Outcome

Each change is listed once, including changes to users, categories and other records that belong to no location.
