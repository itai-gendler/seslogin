---
type: web
actors:
- member
entryPoints:
- {web: /period}
references:
- {kind: code, role: implementation, target: web/src/period/PeriodEdit.tsx}
- {kind: code, role: implementation, target: api/src/period_link.rs}
---

# Time entry link

The page a member reaches from the link in a reminder email, where they check and correct the one period the link was sent for. The link is all the member needs; it opens nothing else.
