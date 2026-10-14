---
kind: alternative
routes:
  web: Web
steps:
- text: The Member opens a "Forgot to sign out?" link, picks a category and gives the time they left
  kind: actor
  actor: member
  entities:
  - {entity: period, effect: reads, facts: [Start time]}
  - {entity: category, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'time-entry-link::time-entry'}
- text: The Product closes the Period
  kind: product
  actor: member
  entities:
  - {entity: period, effect: changes, from: Signed in, to: Signed out, facts: [End time, Category]}
  contexts:
    web: {place: 'time-entry-link::time-entry'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#update_period_time_category}
---

# Sign out after the fact from a link

## Trigger

A member left without signing out.

## Outcome

The period is closed and the member drops off the location's kiosks.
