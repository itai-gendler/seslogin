---
appliesTo:
- {type: capability, id: sign-out-member}
- {type: entity, id: period, facts: [End time]}
references:
- {kind: code, role: implementation, target: web/src/kiosk/ScanState.ts}
- {kind: code, role: implementation, target: web/src/kiosk/components/ScanScreenAdjust.tsx}
---

# A sign-out more than twelve hours after sign-in is questioned

A member scanning out more than twelve hours after signing in is first asked whether they forgot to sign out — answering yes puts the sign-out one hour after the sign-in — and any period longer than twelve hours must be confirmed before it is submitted.
