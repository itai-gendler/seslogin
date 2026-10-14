---
kind: alternative
routes:
  web: Web
steps:
- text: The User accepts the prompt shown after signing in and confirms on their device
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'dashboard::location-dashboard::passkey-prompt'}
- text: The Product saves the Passkey for the User
  kind: product
  actor: user
  entities:
  - {entity: passkey, effect: creates, facts: [Name, Added]}
  - {entity: user, effect: reads, facts: []}
  contexts:
    web: {place: 'dashboard::location-dashboard::passkey-prompt'}
references:
- {kind: code, role: implementation, target: web/src/admin/components/PasskeyEnrollPrompt.tsx}
---

# Add a passkey when prompted after signing in

## Trigger

A user signed in with an emailed code and has no passkey.

## Outcome

The user can sign in with the passkey next time.

## Edge cases

- The user may skip the prompt; it returns no sooner than twelve hours later.
