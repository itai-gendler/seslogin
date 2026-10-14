---
appliesTo:
- {type: entity, id: member, effect: changes, facts: [Given name, Surname, Member ID]}
permits:
- related:
  - {verb: has, entity: location}
  - {verb: has, entity: location-role}
  - {verb: holds, entity: user}
  when:
  - {entity: location-role, fact: Role, is: Admin}
  - {fact: SES record, absent: true}
- actors:
  - super-user
  when:
  - {fact: SES record, absent: true}
- unattended: true
references:
- {kind: code, role: implementation, target: web/src/admin/pages/MembersList.tsx}
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#update_person}
---

# Only a location's admins and super users edit a member, and only one added by hand

A member synced from SES is kept by member sync; an Admin at the member's location, or a super user, changes the names and member ID only of a member added by hand.

## Rationale

SES headquarters is the source of truth for a synced member; a change made here would be overwritten by the next sync.
