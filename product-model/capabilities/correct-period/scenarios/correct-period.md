---
kind: primary
routes:
  web: Web
steps:
- text: The Member opens the link from the reminder and checks the period's location, category and times
  kind: actor
  actor: member
  entities:
  - {entity: period, effect: reads, facts: [Category, Start time, End time]}
  - {entity: location, effect: reads, facts: [Name]}
  - {entity: category, effect: reads, facts: []}
  contexts:
    web: {place: 'time-entry-link::time-entry'}
- text: The Member picks the right category, corrects the times and saves
  kind: actor
  actor: member
  entities:
  - {entity: category, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'time-entry-link::time-entry'}
- text: The Product saves the Period and thanks the Member
  kind: product
  actor: member
  entities:
  - {entity: period, effect: changes, facts: [Start time, End time, Category]}
  contexts:
    web: {place: 'time-entry-link::time-entry'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#update_period_time_category}
- {kind: code, role: implementation, target: web/src/period/PeriodEditForm.tsx}
---

# Correct a period from a reminder

## Trigger

A member was asked to check their time entry.

## Outcome

The period holds what the member says happened; they can make another change while the link lasts.
