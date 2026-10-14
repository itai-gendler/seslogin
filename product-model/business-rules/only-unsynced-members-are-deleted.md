---
appliesTo:
- {type: entity, id: member, effect: changes, to: Deleted}
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
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#delete_person}
---

# Only a location's admins and super users delete a member, and only one added by hand

A synced member is deleted only by member sync once SES no longer lists them; an Admin at the member's location, or a super user, deletes a member added by hand.
