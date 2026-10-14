---
appliesTo:
- {type: entity, id: kiosk, effect: changes, to: Replaced}
permits:
- actors:
  - user
- actors:
  - super-user
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#enroll_session}
---

# Any user enrolling a computer releases it from its earlier kiosk

The user enrolling a computer needs Admin only at the location they enroll it for; the earlier kiosk entry the computer held is released wherever it is, since only that computer ever worked as it.
