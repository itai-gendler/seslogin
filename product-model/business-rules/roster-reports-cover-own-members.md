---
appliesTo:
- {type: capability, id: view-attendance-heatmap}
- {type: capability, id: view-last-seen}
references:
- {kind: code, role: implementation, target: web/src/admin/pages/ActivityHeatmap.tsx}
- {kind: code, role: implementation, target: web/src/admin/pages/ActivityLastSeen.tsx}
---

# The heatmap and last seen cover only the location's own members

They list the members on the location's roster; last seen counts each member's most recent sign-in at any location.
