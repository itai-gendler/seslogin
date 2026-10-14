---
kind: edge
routes:
  web: Web
steps:
- text: The User opens Help and feedback
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'dashboard::location-dashboard::help'}
- text: The Product offers the support email address instead of the form
  kind: condition
  entities:
  - {entity: user, effect: reads, facts: []}
  contexts:
    web: {place: 'dashboard::location-dashboard::help'}
references:
- {kind: code, role: implementation, target: api/src/graphql/query.rs#feedback_available}
---

# Feedback is not available

## Trigger

The support desk is not connected on this deployment.

## Outcome

The user is pointed to the support address.
