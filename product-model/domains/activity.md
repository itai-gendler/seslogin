---
references:
- {kind: code, role: implementation, target: web/src/admin/components/SubmenuBar.tsx}
---

# Activity

The Activity section and the kiosk's sign-ins: periods and guest periods, how they are recorded and corrected, and the reports read from them.

## Boundary

Owns periods, guest periods and reporting on them. It does not own the categories periods are recorded against, which belong to Categories, nor the kiosks they are recorded at.
