---
kind: primary
routes:
  web: Web
steps:
- text: The User enters their email address and passes the human check
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'dashboard::sign-in::login'}
- text: The Product emails a six-digit code valid for ten minutes to the User's address
  kind: product
  actor: user
  entities:
  - {entity: user, effect: reads, facts: [Email, Enabled]}
  contexts:
    web: {place: 'dashboard::sign-in::login'}
- text: The User enters the code
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'dashboard::sign-in::login'}
- text: The Product signs the User in
  kind: product
  actor: user
  entities:
  - {entity: user, effect: reads, facts: [Email]}
  contexts:
    web: {place: 'dashboard::sign-in::login'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#request_auth_code}
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#verify_auth_code}
---

# Sign in with a code from email

## Trigger

A user wants to work in the dashboard.

## Outcome

The user is signed in and reaches their location dashboard.

## Edge cases

- A second code for the same address is not sent within thirty seconds of the first.
