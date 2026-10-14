---
appliesTo:
- {type: capability, id: sign-in-with-email-code}
- {type: capability, id: sign-in-with-passkey}
- {type: entity, id: user, facts: [Enabled]}
references:
- {kind: code, role: implementation, target: api/src/auth.rs}
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#request_auth_code}
---

# A disabled user cannot sign in

A disabled user is sent no code, cannot sign in with a passkey, and loses any session they had, until a super user enables them again.
