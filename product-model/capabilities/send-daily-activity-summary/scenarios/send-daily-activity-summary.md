---
kind: primary
routes:
  web: Web
steps:
- text: It is just after midnight in Sydney
  kind: condition
  unattended: true
  entities: []
  contexts:
    web: {place: 'dashboard::location-dashboard::daily-email'}
- text: The Product emails each User the previous day's periods at their chosen Locations
  kind: product
  entities:
  - {entity: user, effect: reads, facts: [Email, Enabled, Daily email locations, Disaggregate virtual periods]}
  - {entity: location, effect: reads, facts: [Name]}
  - {entity: period, effect: reads, facts: [Start time, End time, Category]}
  - {entity: member, effect: reads, facts: [Given name, Surname]}
  - {entity: category, effect: reads, facts: [Name, Virtual]}
  contexts:
    web: {place: 'dashboard::location-dashboard::daily-email'}
references:
- {kind: code, role: implementation, target: api/src/activity_summary.rs#run}
---

# Email yesterday's activity

## Trigger

A new day starts.

## Outcome

Coordinators see yesterday's activity without opening the dashboard.

## Edge cases

- A user whose locations had no activity that day gets no email.
