---
appliesTo:
- {type: capability, id: sign-out-member}
- {type: capability, id: correct-period}
- {type: entity, id: category, facts: [Enabled]}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#update_period_time_category}
- {kind: code, role: implementation, target: web/src/admin/pages/CategoryList.tsx}
---

# A member picks only an enabled category

Kiosks and reminder links offer only enabled categories; an admin may keep a disabled category on a period that already has it.
