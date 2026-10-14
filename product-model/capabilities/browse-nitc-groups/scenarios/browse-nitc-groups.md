---
kind: primary
routes:
  web: Web
steps:
- text: The Super user opens the NITC groups
  kind: actor
  actor: super-user
  entities:
  - {entity: nitc-group, effect: reads, facts: [NITC type, SES tags]}
  contexts:
    web: {place: 'dashboard::administration::nitc-groups'}
references:
- {kind: code, role: implementation, target: web/src/admin/pages/NitcGroupList.tsx}
---

# Look through the NITC groups

## Trigger

A super user reviews how training is exported.

## Outcome

The super user sees every NITC group.
