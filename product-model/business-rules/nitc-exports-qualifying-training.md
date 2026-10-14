---
appliesTo:
- {type: capability, id: export-training-to-nitc}
- {type: entity, id: period, facts: [NITC export]}
- {type: entity, id: category, facts: [NITC group]}
references:
- {kind: code, role: implementation, target: api/src/nitc_export.rs#assign_period}
---

# Only qualifying periods are exported to NITC

A period is exported when its category belongs to an NITC group, its location is linked to SES and exports to NITC, it started on or after the location's export date, and it lasts no more than 96 hours.
