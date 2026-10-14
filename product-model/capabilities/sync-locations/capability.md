---
availability:
- {place: 'dashboard::administration'}
domain: locations
references:
- {kind: code, role: implementation, target: api/src/location_sync.rs}
---

# Sync locations

Every night the SES units, state headquarters and zones are brought in as locations, and locations whose SES name changed are renamed.
