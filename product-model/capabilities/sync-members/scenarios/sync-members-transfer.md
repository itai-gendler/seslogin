---
kind: alternative
routes:
  web: Web
steps:
- text: A sync of another location finds a member marked missing in that unit's SES roster
  kind: condition
  unattended: true
  entities:
  - {entity: member, effect: reads, facts: [SES record]}
  - {entity: location, effect: reads, facts: []}
  contexts:
    web: {place: 'dashboard::location-dashboard::members'}
- text: The Product moves the Member to the new unit and clears the missing mark
  kind: product
  entities:
  - {entity: member, effect: changes, from: Missing from SES, to: Active, facts: [Home unit, Missing from SES since]}
  contexts:
    web: {place: 'dashboard::location-dashboard::members'}
references:
- {kind: code, role: implementation, target: api/src/member_sync.rs}
---

# A member transfers to another unit

## Trigger

A member moves to another unit in SES.

## Outcome

The member is on the new unit's roster and is never deleted.

## Edge cases

- A member deleted by sync who appears in SES again is restored the same way.
