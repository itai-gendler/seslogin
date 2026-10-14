---
kind: alternative
routes:
  web: Web
steps:
- text: A Period has no NITC Category, is at a Location not exporting, started before the export date or lasts more than 96 hours
  kind: condition
  unattended: true
  entities:
  - {entity: period, effect: reads, facts: [Category, Start time, End time]}
  - {entity: category, effect: reads, facts: [NITC group]}
  - {entity: location, effect: reads, facts: [NITC export from]}
  contexts:
    web: {place: 'dashboard::location-dashboard::previous-periods'}
- text: The Product leaves the Period out of every NITC event, withdrawing it from one it was in
  kind: condition
  entities:
  - {entity: period, effect: reads, facts: [NITC export]}
  contexts:
    web: {place: 'dashboard::location-dashboard::previous-periods'}
references:
- {kind: code, role: implementation, target: api/src/nitc_export.rs}
---

# A period that is not exported

## Trigger

A period changes so it no longer qualifies.

## Outcome

SES no longer lists the member for that event.
