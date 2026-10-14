---
kind: configuration
of: screen
settings:
- {entity: kiosk, fact: Mode}
takesEffect: When the kiosk loads its settings; a change made in the dashboard reaches a running kiosk with its next settings refresh.
stability: The mode stays until an admin changes it; a kiosk's periods are unaffected by the change.
alternatives:
- {id: 'kiosk::enrolled::scan', selectedWhen: Mode is Scan. A kiosk whose settings name no mode is a Scan kiosk.}
- {id: 'kiosk::enrolled::status', selectedWhen: Mode is Status.}
references:
- {kind: code, role: implementation, target: web/src/kiosk/KioskMain.tsx}
- {kind: code, role: implementation, target: web/src/admin/components/SessionForm.tsx}
---

# Kiosk mode

A kiosk either lets members sign in and out or shows a live list of who is signed
in at the location; units run both side by side.
