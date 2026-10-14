---
appliesTo:
- {type: entity, id: kiosk, effect: changes, from: Awaiting setup, to: Active}
permits:
- actors:
  - user
- actors:
  - super-user
references:
- {kind: code, role: implementation, target: api/src/auth.rs#issue_token_for_scan_code}
---

# Whoever holds a kiosk's setup code sets it up

The setup code is the authority: the person who enters it on a computer, normally the user who created the kiosk, sets that kiosk up without signing in.
