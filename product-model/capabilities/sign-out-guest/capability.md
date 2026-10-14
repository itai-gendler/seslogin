---
availability:
- {place: 'kiosk::enrolled'}
domain: activity
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#scan_guest_sign_out}
---

# Sign out a guest

A guest still signed in at the location is signed out from the kiosk's guest list. Exists only while the kiosk's Guests setting is on.
