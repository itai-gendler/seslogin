---
appliesTo:
- {type: capability, id: set-up-kiosk-with-code}
- {type: entity, id: kiosk, facts: [Setup code]}
references:
- {kind: code, role: implementation, target: api/src/auth.rs#issue_token_for_scan_code}
---

# A setup code sets up one computer once

Entering a setup code makes the computer the kiosk and uses the code up; a deleted kiosk's code does not work.
