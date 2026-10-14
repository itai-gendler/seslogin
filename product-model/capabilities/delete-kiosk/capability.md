---
availability:
- {place: 'dashboard::location-dashboard'}
domain: kiosks
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#delete_session}
---

# Delete a kiosk

An admin deletes a kiosk; the computer stops working as a kiosk.
