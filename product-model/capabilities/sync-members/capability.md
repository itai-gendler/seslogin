---
availability:
- {place: 'dashboard::location-dashboard'}
domain: members
references:
- {kind: code, role: implementation, target: api/src/member_sync.rs}
- {kind: doc, role: context, target: CLAUDE.md}
---

# Sync members

Each location linked to an SES headquarters has its roster brought in step with SES once a day: new members are added, changed names, member IDs and units are updated, members who have left are marked missing and deleted after a grace period, and email addresses come from the SES contact directory. An admin can ask for a sync sooner.
