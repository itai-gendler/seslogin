---
appliesTo:
- {type: entity, id: category, effect: changes}
permits:
- actors:
  - super-user
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#update_category}
---

# Only a super user changes a category

Categories are shared by every location.
