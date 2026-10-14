---
appliesTo:
- {type: entity, id: guest-period}
- {type: capability, id: view-activity-totals}
- {type: capability, id: export-training-to-nitc}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#scan_guest_sign_in}
---

# Guest periods never count as a member's time

A guest period has no member and no category, so it appears in the location's lists, who is here and the exported spreadsheet, but never in per-member totals, breakdowns or the NITC export.
