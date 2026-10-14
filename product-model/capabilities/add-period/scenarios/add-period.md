---
kind: primary
routes:
  web: Web
steps:
- text: The User picks a member and a category, enters the start and end times and an optional comment, and saves
  kind: actor
  actor: user
  entities:
  - {entity: member, effect: reads, facts: [Given name, Surname]}
  - {entity: category, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'dashboard::location-dashboard::new-period'}
- text: The Product records the Period at the Location
  kind: product
  actor: user
  entities:
  - {entity: period, effect: creates, to: Signed out, facts: [Start time, End time, Category, Comment, NITC export]}
  - {entity: location, effect: reads, facts: []}
  contexts:
    web: {place: 'dashboard::location-dashboard::new-period'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#create_period}
---

# Record a period for a member

## Trigger

A member attended without using the kiosk.

## Outcome

The period counts in every report, and in the NITC export where its category is exported.
