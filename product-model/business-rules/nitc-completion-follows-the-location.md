---
appliesTo:
- {type: capability, id: export-training-to-nitc}
- {type: entity, id: location, facts: [Complete NITC events on export]}
references:
- {kind: code, role: implementation, target: api/src/nitc_export.rs#should_complete}
---

# Exported NITC events are completed only when the location asks

A location chooses whether its exported events are marked completed in SES or left for its people to review and finish; an event left with no periods is always completed.
