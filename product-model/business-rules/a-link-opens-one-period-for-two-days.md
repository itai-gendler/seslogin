---
appliesTo:
- {type: capability, id: correct-period}
- {type: entity, id: period}
references:
- {kind: code, role: implementation, target: api/src/period_link.rs#issue_period_link_token}
---

# A reminder link opens one period for 48 hours

The link in a reminder reaches only the period it was sent for, works for 48 hours, and stops working if the period is deleted.
