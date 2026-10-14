---
domain: activity
references:
- {kind: code, role: implementation, target: api/src/graphql/query.rs}
- {kind: doc, role: context, target: SCHEMA.md}
---

# Period

One stretch of a member's time at a location, from signing in to signing out, recorded against the activity category that best represents it. A period belongs to the location where it was signed in, whichever unit the member is from.

## Information kept

- **Start time** — when the member signed in, as recorded or as corrected
- **End time** — when the member signed out, as recorded or as corrected
- **Category** — the activity category the time is recorded against
- **Comment** — a note an admin adds to the period
- **Signed in at** — the kiosk the period was signed in at, when it was
- **Signed out at** — the kiosk the period was signed out at, when it was
- **NITC export** — whether the period is waiting to be exported to SES or which NITC event it was exported into

## States

### Signed in

The member is signed in; the period is incomplete until they sign out.

### Signed out

The period has an end time and a category.
