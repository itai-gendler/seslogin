---
entities:
- {entity: member, shows: [Given name, Surname], collects: [Member ID]}
- {entity: period, shows: [Start time, End time]}
- {entity: guest-period, shows: [Guest name, Start time]}
references:
- {kind: code, role: implementation, target: web/src/kiosk/components/ScanScreenMain.tsx}
- {kind: code, role: implementation, target: web/src/kiosk/components/ScanSignedInPanel.tsx}
---

# Scan

The kiosk's main screen, where a member enters their member ID and sees the result of recent sign-ins and sign-outs.
