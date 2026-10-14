---
kind: primary
routes:
  web: Web
steps:
- text: The User ticks the locations they want a daily summary of and saves
  kind: actor
  actor: user
  entities:
  - {entity: user, effect: reads, facts: [Daily email locations]}
  - {entity: location, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'dashboard::location-dashboard::daily-email'}
- text: The Product saves the User's daily email locations
  kind: product
  actor: user
  entities:
  - {entity: user, effect: changes, facts: [Daily email locations]}
  - {entity: location, effect: reads, facts: []}
  contexts:
    web: {place: 'dashboard::location-dashboard::daily-email'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#update_my_email_config}
---

# Choose locations for the daily email

## Trigger

A coordinator wants yesterday's activity in their inbox.

## Outcome

From the next morning the user receives the summary for those locations.

## Edge cases

- Only locations the user holds a role at are offered, Read only included.
