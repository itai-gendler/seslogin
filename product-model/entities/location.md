---
domain: locations
relations:
- {entity: member, verb: has, cardinality: one-to-many}
- {entity: period, verb: has, cardinality: one-to-many}
- {entity: guest-period, verb: has, cardinality: one-to-many}
- {entity: kiosk, verb: has, cardinality: one-to-many}
- {entity: location-role, verb: has, cardinality: one-to-many}
- {entity: audit-log-entry, verb: has, cardinality: one-to-many}
references:
- {kind: code, role: implementation, target: api/src/graphql/query.rs}
- {kind: code, role: implementation, target: api/src/location_sync.rs}
- {kind: doc, role: intent, target: MANUAL.md}
---

# Location

A logical grouping of members — usually one SES unit at one place — with its own kiosks and its own activity log of who signed in and out there.

## Information kept

- **Name** — the location's name
- **Enabled** — whether the location is in use
- **SES headquarters** — the SES unit or headquarters the location's roster and name are synced from
- **Last successful member sync** — when member sync last completed for the location
- **NITC export from** — the date from which periods at the location are exported to SES as NITC events; unset means not exported
- **Complete NITC events on export** — whether exported NITC events are marked completed in SES or left for the unit to finish
