---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Logout
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'dashboard::location-dashboard'}
- text: The Product ends the User's session
  kind: product
  actor: user
  entities:
  - {entity: user, effect: reads, facts: []}
  contexts:
    web: {place: 'dashboard::location-dashboard'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#logout}
---

# Sign out of the dashboard

## Trigger

A user finishes.

## Outcome

The session no longer works and the sign-in page is shown.
