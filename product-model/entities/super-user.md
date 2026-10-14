---
kind: person
acts: external
relations:
- {entity: user, verb: is, cardinality: one-to-one}
references:
- {kind: code, role: implementation, target: api/src/graphql/auth.rs#require_location_access}
---

# Super user

A user who administers SES Activity as a whole: every location, the users, the categories and NITC groups. A super user also reaches every location's dashboard pages with an Admin's abilities.
