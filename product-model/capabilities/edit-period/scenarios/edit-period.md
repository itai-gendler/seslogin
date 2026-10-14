---
kind: primary
routes:
  web: Web
steps:
- text: The User opens a period, changes its category, times or comment and saves
  kind: actor
  actor: user
  entities:
  - {entity: period, effect: reads, facts: [Category, Start time, End time, Comment]}
  - {entity: category, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'dashboard::location-dashboard::period'}
- text: The Product saves the Period
  kind: product
  actor: user
  entities:
  - {entity: period, effect: changes, facts: [Start time, End time, Category, Comment]}
  contexts:
    web: {place: 'dashboard::location-dashboard::period'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#update_period_time_category}
- {kind: code, role: implementation, target: web/src/admin/pages/ActivityEdit.tsx}
---

# Correct a member's period

## Trigger

A member picked the wrong category or times.

## Outcome

Reports and the NITC export reflect the corrected period.

## Edge cases

- A category that has since been disabled may stay on a period that already has it.
