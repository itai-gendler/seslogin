---
availability:
- {place: 'dashboard::location-dashboard'}
domain: settings
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#begin_passkey_registration}
---

# Add a passkey

A user adds a passkey to sign in with, from their settings or from the prompt after signing in with an emailed code.
