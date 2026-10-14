---
kind: alternative
routes:
  web: Web
steps:
- text: The User opens a guest's entry, changes the name, times or comment and saves
  kind: actor
  actor: user
  entities:
  - {entity: guest-period, effect: reads, facts: [Guest name, Start time, End time, Comment]}
  - {entity: guest, effect: reads, facts: []}
  contexts:
    web: {place: 'dashboard::location-dashboard::period'}
- text: The Product saves the Guest period
  kind: product
  actor: user
  entities:
  - {entity: guest-period, effect: changes, facts: [Guest name, Start time, End time, Comment]}
  contexts:
    web: {place: 'dashboard::location-dashboard::period'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#update_guest_period}
---

# Correct a guest period

## Trigger

A guest's name or times were wrong.

## Outcome

The guest's entry is corrected.

## Edge cases

- Closing an open guest period from here signs the guest out.
