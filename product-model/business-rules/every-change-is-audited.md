---
appliesTo:
- {type: entity, id: audit-log-entry}
- {type: entity, id: member, effect: changes}
- {type: entity, id: period, effect: changes}
- {type: entity, id: guest-period, effect: changes}
- {type: entity, id: kiosk, effect: creates}
- {type: entity, id: user, effect: changes}
- {type: entity, id: location, effect: changes}
- {type: entity, id: category, effect: changes}
references:
- {kind: code, role: implementation, target: api/src/audit.rs}
- {kind: doc, role: context, target: CLAUDE.md}
---

# Every change to members, periods, kiosks, users, locations and categories is recorded in the audit log

Each change is recorded with who made it, the locations it touched and each changed field before and after; a change that changes nothing records nothing, and secrets are shown only as redacted.
