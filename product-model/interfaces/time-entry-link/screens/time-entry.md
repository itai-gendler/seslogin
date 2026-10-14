---
entities:
- {entity: period, shows: [Category, Start time, End time], collects: [Category, Start time, End time]}
- {entity: location, shows: [Name]}
- {entity: category, shows: [Name]}
references:
- {kind: code, role: implementation, target: web/src/period/PeriodEditForm.tsx}
- {kind: code, role: implementation, target: web/src/period/PeriodEditConfirmation.tsx}
---

# Check your time entry

The one period the link opens, with its location, category and times; titled "Forgot to sign out?" while the period is still open.
