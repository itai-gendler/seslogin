---
kind: person
acts: external
domain: members
relations:
- {entity: period, verb: has, cardinality: one-to-many}
references:
- {kind: code, role: implementation, target: api/src/graphql/query.rs}
- {kind: code, role: implementation, target: api/src/member_sync.rs}
- {kind: doc, role: intent, target: MANUAL.md}
---

# Member

A volunteer of an SES unit who signs in and out at a kiosk by entering their member ID. A member belongs to one unit's roster but may sign in at any location's kiosk.

## Information kept

- **Given name** — the member's first name
- **Surname** — the member's last name
- **Member ID** — the number the member enters at a kiosk, shown in the dashboard as the SES ID
- **SES record** — the SES headquarters person the member is synced from; absent for a member added by hand
- **Email** — the member's address from the SES contact directory, where reminders about their periods go
- **Home unit** — the location whose roster the member is on
- **Missing from SES since** — when member sync first stopped finding the member in their unit's SES roster

## States

### Active

On their unit's roster and able to sign in.

### Missing from SES

Member sync no longer finds them in their unit's SES roster; they are deleted once the grace period passes unless a later sync finds them again.

### Deleted

Removed from the roster by an admin or by member sync; a later sync that finds them in SES again restores them.
