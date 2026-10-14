---
kind: primary
result: achieved
routes:
  web: Web
steps:
- text: The User signs in with a code emailed to them
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'dashboard::sign-in::login'}
- text: The Product signs the User in
  kind: product
  actor: user
  capability: sign-in-with-email-code
  entities:
  - {entity: user, effect: reads, facts: [Email]}
  contexts:
    web: {place: 'dashboard::sign-in::login'}
- text: The Product shows the add-a-passkey prompt to the User, who has no Passkey
  kind: condition
  entities:
  - {entity: passkey, effect: reads, facts: []}
  - {entity: user, effect: reads, facts: []}
  contexts:
    web: {place: 'dashboard::location-dashboard::passkey-prompt'}
- text: The User accepts the prompt and confirms on their device
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'dashboard::location-dashboard::passkey-prompt'}
- text: The Product saves the Passkey
  kind: product
  actor: user
  capability: register-passkey
  entities:
  - {entity: passkey, effect: creates, facts: [Name, Added]}
  contexts:
    web: {place: 'dashboard::location-dashboard::passkey-prompt'}
references:
- {kind: code, role: implementation, target: web/src/admin/components/PasskeyEnrollPrompt.tsx}
---

# Add a passkey right after signing in with a code

## Trigger

A user without a passkey signs in with an emailed code on a device that supports passkeys.

## Outcome

The user continues to the dashboard with a passkey saved.

## Edge cases

- The prompt is not shown when the user signed in with a passkey, and at most once every twelve hours.
