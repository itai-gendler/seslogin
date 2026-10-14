---
appliesTo:
- {type: capability, id: expire-kiosk}
- {type: capability, id: reactivate-kiosk}
references:
- {kind: code, role: implementation, target: api/src/session_key.rs}
- {kind: code, role: implementation, target: api/src/expire.rs}
---

# A kiosk that makes no contact for two weeks stops working

Every contact keeps a kiosk working for another two weeks. A kiosk set up by QR code that lapses can be reactivated; one set up with a code has to be set up again.
