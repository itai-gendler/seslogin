---
kind: alternative
routes:
  web: Web
steps:
- text: The Member picks a category and changes the sign-in or sign-out date and time before submitting
  kind: actor
  actor: member
  entities:
  - {entity: category, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'kiosk::enrolled::sign-out'}
- text: The Product asks for confirmation when the period is longer than twelve hours
  kind: condition
  entities:
  - {entity: period, effect: reads, facts: [Start time]}
  contexts:
    web: {place: 'kiosk::enrolled::sign-out'}
- text: The Product closes the Period with the adjusted times
  kind: product
  actor: member
  entities:
  - {entity: period, effect: changes, from: Signed in, to: Signed out, facts: [Start time, End time, Category, Signed out at]}
  contexts:
    web: {place: 'kiosk::enrolled::sign-out'}
references:
- {kind: code, role: implementation, target: web/src/kiosk/components/ScanScreenAdjust.tsx}
---

# Adjust the times while signing out

## Trigger

The member arrived earlier or left later than they scanned.

## Outcome

The period records the times the member gave.
