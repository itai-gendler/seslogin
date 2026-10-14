---
appliesTo:
- {type: capability, id: change-daily-email-settings}
- {type: capability, id: send-daily-activity-summary}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#update_my_email_config}
- {kind: code, role: implementation, target: api/src/activity_summary.rs#run}
---

# A daily email covers only locations the user holds a role at

A user chooses daily summaries only of locations they hold a role at, and each summary is checked against their roles when it is sent.
