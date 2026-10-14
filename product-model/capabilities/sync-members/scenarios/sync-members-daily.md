---
kind: primary
routes:
  web: Web
steps:
- text: The location's daily sync hour comes round
  kind: condition
  unattended: true
  entities:
  - {entity: location, effect: reads, facts: [SES headquarters]}
  contexts:
    web: {place: 'dashboard::location-dashboard::members'}
- text: The Product adds members new in SES and updates members whose names, member ID or unit changed
  kind: product
  entities:
  - {entity: member, as: new, effect: creates, to: Active, facts: [Given name, Surname, Member ID, SES record, Home unit]}
  - {entity: member, as: existing, effect: changes, facts: [Given name, Surname, Member ID, Home unit]}
  contexts:
    web: {place: 'dashboard::location-dashboard::members'}
- text: The Product records the sync and then fills in members' email addresses from the SES contact directory
  kind: product
  entities:
  - {entity: location, effect: changes, facts: [Last successful member sync]}
  - {entity: member, as: existing, effect: changes, facts: [Email]}
  contexts:
    web: {place: 'dashboard::location-dashboard::members'}
references:
- {kind: code, role: implementation, target: api/src/member_sync.rs#run}
- {kind: code, role: implementation, target: api/src/bin/dispatcher-lambda.rs}
---

# Sync a location's roster on schedule

## Trigger

Every hour, the locations whose hour it is are synced.

## Outcome

The roster matches SES and the members list shows the time of the sync.

## Edge cases

- A member who is in SES but was added here by hand with the same member ID is left alone.
- A failing contact-directory lookup does not undo the roster changes already made.
