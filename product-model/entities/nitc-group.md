---
domain: categories
relations:
- {entity: category, verb: groups, cardinality: one-to-many}
references:
- {kind: code, role: implementation, target: web/src/admin/pages/NitcGroupEdit.tsx}
- {kind: code, role: implementation, target: api/src/nitc_export.rs}
---

# NITC group

A group of categories exported together into one SES non-incident (NITC) event per location and day, with the NITC type and SES tags that event carries.

## Information kept

- **NITC type** — the SES non-incident type of the events exported for the group
- **SES tags** — the SES non-incident tags those events carry
