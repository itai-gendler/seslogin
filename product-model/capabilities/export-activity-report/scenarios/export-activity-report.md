---
kind: primary
routes:
  web: Web
steps:
- text: The User opens Reports, chooses a range and exports it as CSV or Excel
  kind: actor
  actor: user
  entities:
  - {entity: period, effect: reads, facts: [Start time, End time, Category, Comment, Signed in at, Signed out at]}
  - {entity: guest-period, effect: reads, facts: [Guest name, Start time, End time, Comment]}
  - {entity: member, effect: reads, facts: [Member ID, Given name, Surname]}
  contexts:
    web: {place: 'dashboard::location-dashboard::reports'}
- text: The spreadsheet downloads, guests listed as GUEST
  kind: condition
  entities:
  - {entity: guest, effect: reads, facts: []}
  contexts:
    web: {place: 'dashboard::location-dashboard::reports'}
references:
- {kind: code, role: implementation, target: web/src/admin/pages/Reports.tsx}
---

# Download a spreadsheet of a range

## Trigger

A coordinator needs the raw records for their own reporting.

## Outcome

The user has a spreadsheet of the range.

## Edge cases

- A period whose member or category cannot be loaded is still exported, flagged as incomplete, and the user is warned.
