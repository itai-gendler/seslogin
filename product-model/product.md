---
id: ses-activity
summary: 'Volunteer attendance for SES units: members sign in and out at a kiosk, every period is recorded against an activity category, member rosters sync from SES headquarters, and unit coordinators read reports, export them and get a daily summary.'
category: volunteer-management
tags:
- attendance
- volunteers
- emergency-services
- kiosk
- time-tracking
authors:
- {name: NSW SES Members, url: 'https://github.com/NSWSESMembers'}
license: MIT
languages:
- en
limitations:
- 'Members never sign in to SES Activity themselves: they sign in and out only at an enrolled kiosk by entering their member ID, and correct an entry only through a link their unit emails them.'
- 'A period belongs to one location: signing out at another location''s kiosk opens a new period there instead of closing the first.'
- Members of a unit synced from SES headquarters come from the SES roster; the dashboard does not edit or delete a synced member.
- Dashboard users are created by a super user; there is no self sign-up and no password, only an emailed code or a passkey.
- Kiosks offer the categories built into the kiosk; a category added in the dashboard is not offered at kiosks until the kiosk's own list includes it.
references:
- {kind: doc, role: intent, target: README.md, title: README}
- {kind: doc, role: intent, target: MANUAL.md, title: Operator manual}
- {kind: doc, role: context, target: CLAUDE.md, title: Architecture notes}
- {kind: doc, role: context, target: SCHEMA.md, title: Data model reference}
---

# SES Activity

SES Activity tracks volunteer attendance for State Emergency Service units with as
little friction as possible. A computer or tablet at the unit is enrolled as a
kiosk; a member types their member ID to sign in, and types it again to sign out,
picking the activity category that best represents their time and adjusting the
times if they need to. Members visiting from another unit sign in the same way,
and visitors without a membership record can be signed in by name. Unit
coordinators use the dashboard to manage their members and kiosks, review and
correct periods, and read totals, breakdowns, a heatmap and exports; member
rosters and unit names come from the SES headquarters system, and periods in
training categories are exported back to it as NITC events.

## Intent

"A web app for tracking volunteer attendance with as little friction as
possible." Members check in and out at a kiosk designed for fast, unattended
use, sessions are recorded with activity categories (training, rescue,
operational roles and more), and detailed reporting is available for
coordinators, with members imported automatically from the SES headquarters
API.
