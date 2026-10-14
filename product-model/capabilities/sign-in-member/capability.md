---
availability:
- {place: 'kiosk::enrolled'}
domain: activity
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#scan_register2}
- {kind: doc, role: intent, target: MANUAL.md}
---

# Sign in a member

A member enters their member ID at a kiosk; if they are not already signed in at that kiosk's location, they are signed in there.
