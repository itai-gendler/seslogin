---
kind: alternative
routes:
  web: Web
steps:
- text: The User chooses Sync now on the members list
  kind: actor
  actor: user
  entities:
  - {entity: location, effect: reads, facts: [Last successful member sync]}
  - {entity: member, effect: reads, facts: []}
  contexts:
    web: {place: 'dashboard::location-dashboard::members'}
- text: The Product queues the Location's sync, which then runs as on schedule
  kind: product
  actor: user
  entities:
  - {entity: location, effect: reads, facts: [SES headquarters]}
  contexts:
    web: {place: 'dashboard::location-dashboard::members'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#enqueue_member_sync}
- {kind: code, role: implementation, target: web/src/admin/pages/MembersList.tsx}
---

# Sync a location now

## Trigger

A new member needs to sign in today.

## Outcome

The sync runs within moments instead of at the location's hour.

## Edge cases

- Sync now is offered only when the location is linked to SES and has not synced in the last hour.
