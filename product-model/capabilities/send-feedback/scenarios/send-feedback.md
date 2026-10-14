---
kind: primary
routes:
  web: Web
steps:
- text: The User opens Help and feedback, writes a subject and message and sends it
  kind: actor
  actor: user
  entities:
  - {entity: user, effect: reads, facts: [Email]}
  contexts:
    web: {place: 'dashboard::location-dashboard::help'}
- text: The Product files the message as a support ticket replying to the User's email and shows its reference
  kind: product
  actor: user
  entities:
  - {entity: user, effect: reads, facts: [Email]}
  contexts:
    web: {place: 'dashboard::location-dashboard::help'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#submit_feedback}
---

# Send a help request

## Trigger

A user needs help or has a suggestion.

## Outcome

The user has a ticket reference; replies come by email.
