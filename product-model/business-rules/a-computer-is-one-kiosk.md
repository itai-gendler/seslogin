---
appliesTo:
- {type: capability, id: enroll-kiosk}
- {type: entity, id: kiosk, facts: [Device key]}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#enroll_session}
---

# A computer is one kiosk at a time

Enrolling a computer by QR code releases it from any kiosk entry it held, at whatever location; that entry stays listed there as replaced and never works again.
