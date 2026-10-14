---
kind: alternative
routes:
  web: Web
steps:
- text: The Member enters their member ID more than twelve hours after signing in
  kind: actor
  actor: member
  entities: []
  contexts:
    web: {place: 'kiosk::enrolled::scan'}
- text: The Product asks whether they forgot to sign out
  kind: condition
  entities:
  - {entity: period, effect: reads, facts: [Start time]}
  contexts:
    web: {place: 'kiosk::enrolled::sign-out'}
- text: The Member answers that they forgot
  kind: actor
  actor: member
  entities: []
  contexts:
    web: {place: 'kiosk::enrolled::sign-out'}
- text: The Member picks a category and submits with the sign-out time set to one hour after they signed in
  kind: actor
  actor: member
  entities:
  - {entity: category, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'kiosk::enrolled::sign-out'}
- text: The Product closes the Period one hour after it started
  kind: product
  actor: member
  entities:
  - {entity: period, effect: changes, from: Signed in, to: Signed out, facts: [End time, Category, Signed out at]}
  contexts:
    web: {place: 'kiosk::enrolled::sign-out'}
references:
- {kind: code, role: implementation, target: web/src/kiosk/components/ScanScreenForgotSignOut.tsx}
- {kind: code, role: implementation, target: web/src/kiosk/ScanState.ts}
---

# Sign out after forgetting to

## Trigger

A member left without signing out and comes back the next time.

## Outcome

The forgotten period is closed at a plausible time; the member can sign in again for today.

## Edge cases

- Answering that it really was a long entry signs them out now, after the twelve-hour confirmation.
