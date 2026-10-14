---
kind: validation
routes:
  web: Web
steps:
- text: The User enters a code that is wrong or more than ten minutes old
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'dashboard::sign-in::login'}
- text: The Product refuses the sign-in
  kind: condition
  entities:
  - {entity: user, effect: reads, facts: []}
  contexts:
    web: {place: 'dashboard::sign-in::login'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#verify_auth_code}
---

# Enter a wrong or expired code

## Trigger

The code was mistyped or arrived too late.

## Outcome

The user is not signed in; after five wrong tries the code stops working.
