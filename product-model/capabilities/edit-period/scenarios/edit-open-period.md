---
kind: alternative
routes:
  web: Web
steps:
- text: The User opens a period that is still signed in, sets its category and end time and saves
  kind: actor
  actor: user
  entities:
  - {entity: period, effect: reads, facts: [Start time]}
  - {entity: category, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'dashboard::location-dashboard::period'}
- text: The Product closes the Period
  kind: product
  actor: user
  entities:
  - {entity: period, effect: changes, from: Signed in, to: Signed out, facts: [End time, Category, Comment]}
  contexts:
    web: {place: 'dashboard::location-dashboard::period'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#update_period_time_category}
---

# Close an open period from the dashboard

## Trigger

A member forgot to sign out.

## Outcome

The member is signed out and drops off the location's kiosks at once.
