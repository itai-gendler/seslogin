---
kind: primary
routes:
  web: Web
steps:
- text: The Super user opens Categories, optionally showing disabled ones
  kind: actor
  actor: super-user
  entities:
  - {entity: category, effect: reads, facts: [Name, Enabled, Virtual, NITC group, NITC participant type]}
  contexts:
    web: {place: 'dashboard::administration::categories'}
references:
- {kind: code, role: implementation, target: web/src/admin/pages/CategoryList.tsx}
---

# Look through the categories

## Trigger

A super user reviews the categories.

## Outcome

The super user sees every category and any kiosk category that would record against a missing or disabled one.
