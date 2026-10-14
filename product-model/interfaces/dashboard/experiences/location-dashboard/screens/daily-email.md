---
entities:
- {entity: user, shows: [Daily email locations], collects: [Daily email locations]}
- {entity: location, shows: [Name]}
references:
- {kind: code, role: implementation, target: web/src/admin/pages/SettingsDailyEmail.tsx}
---

# Daily email summary

Which of the user's locations they are emailed a summary of each morning.
