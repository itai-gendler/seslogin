---
availability:
- {place: 'dashboard::location-dashboard'}
domain: activity
references:
- {kind: code, role: implementation, target: api/src/nitc_export.rs}
- {kind: code, role: implementation, target: api/src/bin/nitc-export-lambda.rs}
---

# Export training to NITC

Periods in categories that belong to an NITC group, at locations exporting to NITC, are exported to the SES headquarters system as non-incident (NITC) events — one event per location, NITC group and day, with each member as a participant — and kept in step as periods change.
