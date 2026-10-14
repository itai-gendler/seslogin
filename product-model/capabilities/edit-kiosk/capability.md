---
availability:
- {place: 'dashboard::location-dashboard'}
domain: kiosks
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#update_session}
---

# Edit a kiosk

An admin changes a kiosk's name, mode, options and health check URL, and reads its diagnostics.
