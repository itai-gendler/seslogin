---
entities:
- {entity: audit-log-entry, shows: [When, Who, Action, What, Location, Changes, IP address]}
references:
- {kind: code, role: implementation, target: web/src/admin/pages/AuditLog.tsx}
---

# Audit log

Changes made at the location, newest first; super users can also see every location's changes.
