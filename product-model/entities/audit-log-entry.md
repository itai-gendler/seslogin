---
references:
- {kind: code, role: implementation, target: api/src/audit.rs}
- {kind: code, role: implementation, target: api/src/graphql/audit_log.rs}
---

# Audit log entry

One recorded change: who made it, what changed and when. A change touching two locations, such as a member moving units, is in both locations' logs.

## Information kept

- **When** — when the change was made
- **Who** — the user, kiosk, API token, edit link or background job that made it
- **Action** — created, updated, deleted or restored
- **What** — the kind of record and its name at the time
- **Location** — the location the change belongs to; none for records that belong to no location
- **Changes** — each changed field before and after, with secrets shown only as redacted
- **IP address** — the address the change came from
