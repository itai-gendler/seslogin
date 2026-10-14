---
references:
- {kind: code, role: implementation, target: web/src/admin/pages/MembersList.tsx}
---

# Members

The Members section: a location's roster, kept by hand or synced from SES headquarters.

## Boundary

Owns members and keeping the roster in step with SES. It does not own the periods members record, which belong to Activity.
