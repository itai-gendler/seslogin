---
references:
- {kind: code, role: implementation, target: web/src/admin/components/SubmenuBar.tsx}
---

# Settings

A user's own Settings section: passkeys, the daily email summary and how activity is displayed to them.

## Boundary

Owns each user's own settings. It does not own other users or their roles, which belong to Users.
