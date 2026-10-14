---
appliesTo:
- {type: entity, id: category, effect: creates}
permits:
- actors:
  - super-user
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#create_category}
---

# Only a super user adds a category

Categories are shared by every location.
