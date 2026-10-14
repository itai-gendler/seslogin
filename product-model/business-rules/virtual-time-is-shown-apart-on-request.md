---
appliesTo:
- {type: entity, id: category, facts: [Virtual]}
- {type: entity, id: user, facts: [Disaggregate virtual periods]}
references:
- {kind: code, role: implementation, target: web/src/admin/pages/SettingsActivityDisplay.tsx}
---

# Virtual time is shown separately for users who ask

A user who turns on Disaggregate virtual periods sees time in virtual categories apart from other time in their dashboard, totals, lists and daily email.
