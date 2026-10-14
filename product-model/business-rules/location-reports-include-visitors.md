---
appliesTo:
- {type: capability, id: browse-periods}
- {type: capability, id: view-activity-totals}
- {type: capability, id: view-activity-breakdown}
- {type: capability, id: view-daily-breakdown}
- {type: capability, id: export-activity-report}
references:
- {kind: code, role: implementation, target: web/src/admin/pages/ActivityTotals.tsx}
---

# A location's activity reports include everyone who signed in there

Periods, totals, breakdowns, the daily breakdown and the exported spreadsheet include members visiting from other units.
