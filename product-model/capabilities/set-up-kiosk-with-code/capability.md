---
availability:
- {place: 'kiosk::setup'}
domain: kiosks
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#auth_session}
- {kind: doc, role: intent, target: MANUAL.md}
---

# Set up a kiosk with a code

A computer becomes a location's kiosk when someone enters the six-digit setup code a user created for it. The code works once; the kiosk then stays set up while it keeps making contact.
