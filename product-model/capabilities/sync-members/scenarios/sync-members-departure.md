---
kind: alternative
routes:
  web: Web
steps:
- text: A sync no longer finds an active synced member in their unit's SES roster
  kind: condition
  unattended: true
  entities:
  - {entity: member, effect: reads, facts: [SES record]}
  contexts:
    web: {place: 'dashboard::location-dashboard::members'}
- text: The Product marks the Member missing from SES
  kind: product
  entities:
  - {entity: member, effect: changes, from: Active, to: Missing from SES, facts: [Missing from SES since]}
  contexts:
    web: {place: 'dashboard::location-dashboard::members'}
- text: Seven days later the member is still missing
  kind: condition
  entities:
  - {entity: member, effect: reads, facts: [Missing from SES since]}
  contexts:
    web: {place: 'dashboard::location-dashboard::members'}
- text: The Product deletes the Member
  kind: product
  entities:
  - {entity: member, effect: changes, from: Missing from SES, to: Deleted, facts: []}
  contexts:
    web: {place: 'dashboard::location-dashboard::members'}
references:
- {kind: code, role: implementation, target: api/src/member_sync.rs#plan_absence_changes}
- {kind: code, role: implementation, target: api/src/member_sync.rs#classify_missing}
---

# A member leaves the unit in SES

## Trigger

SES drops a person from the unit's roster.

## Outcome

The member is shown as pending deletion for a week and then removed.

## Edge cases

- Deletion waits if the location's previous successful sync is more than 36 hours old.
