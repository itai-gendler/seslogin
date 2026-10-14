---
kind: person
acts: external
domain: users
relations:
- {entity: location-role, verb: holds, cardinality: one-to-many}
- {entity: passkey, verb: has, cardinality: one-to-many}
references:
- {kind: code, role: implementation, target: api/src/graphql/query.rs}
- {kind: doc, role: intent, target: MANUAL.md}
---

# User

A person who signs in to the dashboard to administer or view one or more locations — the location administrator of the operator manual. What a user may do at a location depends on the Location role they hold there. Users cannot sign in and out at a kiosk as users; most also have a Member record at their own unit.

## Information kept

- **Email** — the address the user signs in with and where their codes and summaries go
- **Super user** — whether the user is also a super user
- **Developer** — whether the user sees features still on trial
- **Enabled** — whether the user can sign in at all
- **Last access** — when the user last used the dashboard
- **Daily email locations** — the locations whose previous day of activity the user is emailed each morning
- **Disaggregate virtual periods** — whether the user's reports show time in virtual categories separately
