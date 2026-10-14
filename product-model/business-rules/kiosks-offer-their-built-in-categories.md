---
appliesTo:
- {type: capability, id: sign-out-member}
- {type: capability, id: add-category}
references:
- {kind: code, role: implementation, target: web/src/lib/categories.ts}
- {kind: code, role: implementation, target: web/src/admin/pages/CategoryList.tsx}
---

# Kiosks offer the categories built into the kiosk

The kiosk's category list, grouped under headings such as Training, is part of the kiosk itself; adding or enabling a category in the dashboard does not add it at kiosks.
