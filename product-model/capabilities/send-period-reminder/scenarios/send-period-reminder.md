---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Remind beside a member's period
  kind: actor
  actor: user
  entities:
  - {entity: period, effect: reads, facts: [Start time, End time, Category]}
  - {entity: member, effect: reads, facts: []}
  contexts:
    web: {place: 'dashboard::location-dashboard::previous-periods'}
- text: The Product emails the Member a reminder with the period's location, category and times and a link to correct it
  kind: product
  actor: user
  entities:
  - {entity: member, effect: reads, facts: [Given name, Email]}
  - {entity: period, effect: reads, facts: [Start time, End time, Category]}
  - {entity: location, effect: reads, facts: [Name]}
  - {entity: category, effect: reads, facts: []}
  contexts:
    web: {place: 'dashboard::location-dashboard::previous-periods'}
- text: The dashboard shows the address the reminder went to
  kind: condition
  entities:
  - {entity: member, effect: reads, facts: [Email]}
  contexts:
    web: {place: 'dashboard::location-dashboard::previous-periods'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#send_period_edit_link}
- {kind: code, role: implementation, target: api/src/period_link.rs}
---

# Remind a member to check a period

## Trigger

A period looks wrong and the member is the one who knows.

## Outcome

The member has a link to correct the period.

## Edge cases

- Each press issues a fresh link, so a member who lost one just needs another reminder.
