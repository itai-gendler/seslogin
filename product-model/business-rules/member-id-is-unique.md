---
appliesTo:
- {type: capability, id: add-member}
- {type: capability, id: edit-member}
- {type: entity, id: member}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#ensure_registration_number_available}
---

# No two members who are not deleted share a member ID

A member ID identifies one member at every kiosk, so adding or changing a member is refused while another member who is not deleted has the same ID.
