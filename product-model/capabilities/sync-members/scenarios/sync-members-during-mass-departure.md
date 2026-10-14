---
kind: edge
routes:
  web: Web
steps:
- text: A sync finds more members missing than the allowed share of the roster
  kind: condition
  unattended: true
  entities:
  - {entity: member, effect: reads, facts: [SES record]}
  - {entity: location, effect: reads, facts: [SES headquarters]}
  contexts:
    web: {place: 'dashboard::location-dashboard::members'}
- text: The Product stops that location's sync without changing anything and leaves it for a person to look at
  kind: condition
  entities:
  - {entity: location, effect: reads, facts: [Last successful member sync]}
  contexts:
    web: {place: 'dashboard::location-dashboard::members'}
references:
- {kind: code, role: implementation, target: api/src/member_sync.rs#absence_candidate_cap}
---

# Too many members would be marked missing

## Trigger

SES returns a roster far smaller than the location's.

## Outcome

The roster is untouched and the last successful sync time does not move.
