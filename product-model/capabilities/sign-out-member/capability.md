---
availability:
- {place: 'kiosk::enrolled'}
domain: activity
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#scan_sign_out}
- {kind: doc, role: intent, target: MANUAL.md}
---

# Sign out a member

A member who is signed in at a kiosk's location enters their member ID again, picks the category that best represents their time, checks or adjusts the times and submits.
