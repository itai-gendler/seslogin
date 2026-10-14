---
availability:
- {place: 'dashboard::location-dashboard'}
domain: kiosks
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#create_session}
- {kind: doc, role: intent, target: MANUAL.md}
---

# Create a kiosk with a setup code

An admin creates a kiosk for the location, chooses its mode and options, and is shown the six-digit code to enter on the computer.
