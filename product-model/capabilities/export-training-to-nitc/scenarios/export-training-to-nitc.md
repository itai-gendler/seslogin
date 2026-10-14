---
kind: primary
routes:
  web: Web
steps:
- text: A Period at an exporting Location is signed out, added, edited or deleted
  kind: condition
  unattended: true
  entities:
  - {entity: period, effect: reads, facts: [Category, Start time, End time]}
  - {entity: location, effect: reads, facts: [NITC export from, SES headquarters]}
  - {entity: category, effect: reads, facts: [NITC group, NITC participant type]}
  contexts:
    web: {place: 'dashboard::location-dashboard::previous-periods'}
- text: The Product puts the Period in the location's NITC event for its NITC group and day and sends the event to SES
  kind: product
  entities:
  - {entity: period, effect: changes, facts: [NITC export]}
  - {entity: nitc-group, effect: reads, facts: [NITC type, SES tags]}
  - {entity: location, effect: reads, facts: []}
  contexts:
    web: {place: 'dashboard::location-dashboard::previous-periods'}
- text: The event is marked completed in SES when the Location completes events on export
  kind: condition
  entities:
  - {entity: location, effect: reads, facts: [Complete NITC events on export]}
  contexts:
    web: {place: 'dashboard::location-dashboard::previous-periods'}
references:
- {kind: code, role: implementation, target: api/src/nitc_export.rs#assign_period}
- {kind: code, role: implementation, target: api/src/nitc_export.rs#sync_nitc_event}
---

# Export a day's training to an NITC event

## Trigger

Members' training time is recorded at the unit.

## Outcome

SES holds the day's training with every member who attended, and the period shows the event it was exported into.

## Edge cases

- A period whose category or day changes moves to the matching event, and the event it left drops the participant.
- An event left with no periods is renamed unused and completed.
