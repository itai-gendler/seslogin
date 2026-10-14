---
appliesTo:
- {type: capability, id: export-training-to-nitc}
- {type: entity, id: nitc-group}
references:
- {kind: code, role: implementation, target: api/src/nitc_export.rs#assign_period}
---

# Each location has one NITC event per NITC group and day

Periods are grouped by location, NITC group and the day they started in Sydney time; each member in the group that day is a participant of the one event.
