---
appliesTo:
- {type: capability, id: sync-members}
- {type: entity, id: member, facts: [Missing from SES since]}
references:
- {kind: code, role: implementation, target: api/src/member_sync.rs#classify_missing}
- {kind: doc, role: context, target: CLAUDE.md}
---

# A member missing from SES is deleted only after seven days

Member sync marks a member SES no longer lists as missing, clears the mark if any location's sync finds them again, and deletes them once the mark is seven days old — and only while the location's previous successful sync is less than 36 hours old.

## Rationale

SES signals a departure only by leaving the person out; a member transferring to another unit is missing from the old unit until the new unit's sync, within the same day, finds them.
