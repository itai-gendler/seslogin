---
domain: categories
relations:
- {entity: period, verb: classifies, cardinality: one-to-many}
references:
- {kind: code, role: implementation, target: api/src/graphql/query.rs}
- {kind: code, role: implementation, target: web/src/lib/categories.ts}
---

# Category

An activity category a period is recorded against — a kind of training, rescue, operational or support activity.

## Information kept

- **Name** — the category's name
- **Enabled** — whether the category can be picked for an entry; a period keeps a category that is later disabled
- **Virtual** — whether time in the category is virtual (remote) activity, which reports can show separately
- **NITC group** — the NITC group whose SES event the category's periods are exported into; none means the category is not exported
- **NITC participant type** — the participant type a member's time in the category is exported with
