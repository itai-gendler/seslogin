---
type: web
actors:
- user
- super-user
entryPoints:
- {web: /admin}
references:
- {kind: code, role: implementation, target: web/src/admin/AdminApp.tsx}
- {kind: code, role: implementation, target: web/src/admin/components/MenuBar.tsx}
- {kind: doc, role: intent, target: MANUAL.md}
---

# Dashboard

The administrators' dashboard ("Dash"): where users manage the members, periods and kiosks of the locations they hold a role at and read their reports, and where super users administer locations, users and categories.
