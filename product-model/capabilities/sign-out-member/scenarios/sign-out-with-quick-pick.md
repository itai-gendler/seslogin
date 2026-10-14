---
kind: alternative
routes:
  web: Web
steps:
- text: The kiosk has quick pick categories on
  kind: condition
  entities:
  - {entity: kiosk, effect: reads, facts: [Quick pick categories]}
  contexts:
    web: {place: 'kiosk::enrolled::scan'}
- text: The Member enters their member ID
  kind: actor
  actor: member
  entities: []
  contexts:
    web: {place: 'kiosk::enrolled::scan'}
- text: The Product offers the Categories recently used at this Location and by this Member
  kind: condition
  entities:
  - {entity: category, effect: reads, facts: [Name]}
  - {entity: location, effect: reads, facts: []}
  - {entity: member, effect: reads, facts: []}
  contexts:
    web: {place: 'kiosk::enrolled::sign-out'}
- text: The Member picks one of the suggested categories and submits the times
  kind: actor
  actor: member
  entities:
  - {entity: category, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'kiosk::enrolled::sign-out'}
- text: The Product closes the Period with that category
  kind: product
  actor: member
  entities:
  - {entity: period, effect: changes, from: Signed in, to: Signed out, facts: [End time, Category, Signed out at]}
  - {entity: category, effect: reads, facts: []}
  contexts:
    web: {place: 'kiosk::enrolled::sign-out'}
references:
- {kind: code, role: implementation, target: api/src/graphql/query.rs#build_quick_pick}
- {kind: code, role: implementation, target: web/src/kiosk/components/ScanScreenQuickPick.tsx}
---

# Sign out with a quick pick

## Trigger

The kiosk has quick pick categories turned on.

## Outcome

The period is closed with a category people at the location have been using, so entries converge.

## Edge cases

- The member can skip the suggestions and choose from the full list.
- Suggestions show the first names of up to three people who most recently picked the category here.
- If the suggestions cannot be worked out the full list is shown instead.
