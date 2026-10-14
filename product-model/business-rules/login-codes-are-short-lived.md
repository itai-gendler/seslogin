---
appliesTo:
- {type: capability, id: sign-in-with-email-code}
- {type: entity, id: user, facts: [Email]}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#request_auth_code}
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#verify_auth_code}
---

# A login code works for ten minutes and five tries

Each code is six digits, expires after ten minutes, stops working after five wrong tries, and a new one is sent at most every thirty seconds.
