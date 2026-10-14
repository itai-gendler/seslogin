---
domain: activity
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#scan_guest_sign_in}
---

# Guest period

A guest's visit to a location, signed in and out by name at a kiosk. It has no member and no category, so it never appears in per-member views or in the NITC export.

## Information kept

- **Guest name** — the name the guest gave
- **Comment** — the reason for the visit given at sign-in, or a note an admin adds
- **Start time** — when the guest signed in
- **End time** — when the guest signed out
- **Signed in at** — the kiosk the guest signed in at
- **Signed out at** — the kiosk the guest signed out at

## States

### Signed in

The guest is at the location.

### Signed out

The guest has left.
