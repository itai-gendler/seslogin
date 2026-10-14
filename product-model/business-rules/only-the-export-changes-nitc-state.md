---
appliesTo:
- {type: entity, id: period, effect: changes, facts: [NITC export]}
permits:
- unattended: true
references:
- {kind: code, role: implementation, target: api/src/nitc_export.rs#assign_period}
---

# Only the NITC export changes a period's NITC export state

Whether a period is waiting for export or which NITC event it is in is set by the export alone.
