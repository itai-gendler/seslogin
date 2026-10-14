---
actors:
- user
- super-user
access: authenticated
entryPoints:
- {dashboard: /admin}
references:
- {kind: code, role: implementation, target: web/src/admin/Layout.tsx}
- {kind: code, role: implementation, target: web/src/admin/components/LocationSelector.tsx}
---

# Location dashboard

A signed-in user's dashboard for one of their locations at a time — its members, activity, reports, kiosks and audit log — together with their own settings. Read only users see it without the controls that change anything.
