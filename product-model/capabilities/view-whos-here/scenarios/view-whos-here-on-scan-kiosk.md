---
kind: alternative
routes:
  web: Web
steps:
- text: The kiosk's Who's here setting is Button or Always visible
  kind: condition
  entities:
  - {entity: kiosk, effect: reads, facts: [Who's here]}
  contexts:
    web: {place: 'kiosk::enrolled::scan'}
- text: The Guest opens the Who's here list beside the scan screen
  kind: actor
  actor: guest
  entities:
  - {entity: member, effect: reads, facts: [Given name, Surname]}
  - {entity: period, effect: reads, facts: [Start time]}
  - {entity: guest-period, effect: reads, facts: [Guest name, Start time]}
  contexts:
    web: {place: 'kiosk::enrolled::scan'}
references:
- {kind: code, role: implementation, target: web/src/kiosk/components/ScanSignedInPanel.tsx}
- {kind: code, role: implementation, target: web/src/kiosk/components/ScanStatusDialog.tsx}
---

# Check who's here on a scan kiosk

## Trigger

Someone at the kiosk wants to know who is already in.

## Outcome

The same list is shown without giving up the kiosk.
