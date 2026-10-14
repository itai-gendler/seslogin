---
availability:
- {place: 'kiosk::enrolled'}
domain: activity
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#scan_guest_sign_in}
- {kind: code, role: implementation, target: web/src/admin/components/SessionForm.tsx}
---

# Sign in a guest

At a kiosk with guests turned on, a visitor without a membership record is signed in by name, optionally with the reason for the visit. Exists only while the kiosk's Guests setting is on.
