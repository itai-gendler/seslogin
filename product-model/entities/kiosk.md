---
domain: kiosks
relations:
- {entity: period, verb: signs in, cardinality: one-to-many}
- {entity: guest-period, verb: starts, cardinality: one-to-many}
references:
- {kind: code, role: implementation, target: api/src/graphql/query.rs}
- {kind: code, role: implementation, target: api/src/session_key.rs}
- {kind: doc, role: intent, target: MANUAL.md}
---

# Kiosk

A computer or tablet registered to one location, where members sign in and out or where who is signed in is shown. A location can have several kiosks; a member may sign in at one and out at another.

## Information kept

- **Name** — a name describing the place or the computer
- **Mode** — Scan, where members sign in and out, or Status, a live list of who is signed in at the location
- **Guests** — whether the kiosk offers signing guests in and out by name
- **Quick pick categories** — whether signing out first offers the location's and the member's recently used categories
- **Who's here** — Off, Button or Always visible: whether the scan screen shows who is signed in at the location
- **Health check URL** — an address the Product calls while the kiosk is in contact, so an outside monitor can tell it is alive
- **Setup code** — the six-digit code that sets up a kiosk created with a code; it works once
- **Device key** — the fingerprint of the key a kiosk set up by QR code signs in with
- **Last contact** — when the kiosk last reached the Product
- **Expires** — when a kiosk set up by QR code stops working if it does not make contact
- **Diagnostics** — what the kiosk last reported about itself: its version, environment, screen, display mode, clock and contact failures

## States

### Awaiting setup

Created with a setup code that has not yet been entered on a computer.

### Active

Set up on a computer and working.

### Expired

A kiosk set up by QR code that has not made contact for two weeks; it stops working until reactivated.

### Replaced

Its computer has since been set up again by scanning its QR code, which moved the computer onto another kiosk entry; it never comes back.
