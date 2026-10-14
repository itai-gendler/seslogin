---
scope: The SES Activity GraphQL API, kiosk, dashboard and time-entry-link web front ends, and the member sync, location sync, NITC export and daily summary jobs.
method: Static inspection of source and documentation at commit 78ac04bf; nothing was run.
covered:
- description: GraphQL queries, mutations, guards and the audit log reader.
  paths:
  - api/src/graphql/
  - api/schema.graphql
- description: Authentication of users, kiosks and edit links, kiosk keys and enrollment, and token expiry.
  paths:
  - api/src/auth.rs
  - api/src/jwt.rs
  - api/src/session_key.rs
  - api/src/expire.rs
  - api/src/period_link.rs
  - api/src/nonce.rs
- description: Audit recording around every business write.
  paths:
  - api/src/audit.rs
- description: Member sync from SES headquarters and its hourly dispatcher.
  paths:
  - api/src/member_sync.rs
  - api/src/ses_api.rs
  - api/src/bin/sync-members.rs
  - api/src/bin/sync-members-lambda.rs
  - api/src/bin/dispatcher-lambda.rs
- description: Location sync from SES headquarters.
  paths:
  - api/src/location_sync.rs
  - api/src/bin/sync-locations.rs
  - api/src/bin/sync-locations-lambda.rs
- description: NITC export of training periods to SES.
  paths:
  - api/src/nitc_export.rs
  - api/src/bin/nitc-export.rs
  - api/src/bin/nitc-export-lambda.rs
- description: Daily activity summary email.
  paths:
  - api/src/activity_summary.rs
  - api/src/bin/activity-summary.rs
  - api/src/bin/activity-summary-lambda.rs
- description: 'Kiosk front end: setup, enrollment, scanning, sign-out, guests and status.'
  paths:
  - web/src/kiosk/
- description: 'Dashboard front end: sign-in, location pages, reports, kiosks, settings and super-user administration.'
  paths:
  - web/src/admin/
  - web/src/enroll/
- description: Member-facing time entry link page.
  paths:
  - web/src/period/
- description: Kiosk category list and front-end helpers.
  paths:
  - web/src/lib/
  - web/src/Router.tsx
- description: Schedules of the background jobs.
  paths:
  - infra/scheduler.tf
exclusions:
- description: Infrastructure, deployment workflows and local development tooling.
  paths:
  - infra/
  - .github/
  - local/
  - Makefile
  - pagination-test/
- description: Database, queue, mail and realtime adapters and their mocks.
  paths:
  - api/src/dynamodb.rs
  - api/src/db.rs
  - api/src/mockdb.rs
  - api/src/mockqueue.rs
  - api/src/mockmail.rs
  - api/src/mockrealtime.rs
  - api/src/sqs.rs
  - api/src/queue.rs
  - api/src/sesmail.rs
  - api/src/mail.rs
  - api/src/ably.rs
  - api/src/realtime.rs
- description: Server wiring, telemetry, request metrics and developer binaries.
  paths:
  - api/src/server.rs
  - api/src/app.rs
  - api/src/telemetry.rs
  - api/src/request_metrics.rs
  - api/src/bin/poem.rs
  - api/src/bin/poem-local.rs
  - api/src/bin/lambda/
  - api/src/bin/export-schema.rs
  - api/src/bin/local-seed.rs
  - api/src/bin/local-tables.rs
  - api/src/bin/pagination-test-server.rs
  - api/src/local_dev.rs
- description: Shared UI components, component demos and the public home page.
  paths:
  - web/src/components/
  - web/src/demo/
  - web/src/home/
  - web/src/assets/
- description: Stale member-sync alerting to the operators.
  paths:
  - api/src/bin/checker-lambda.rs
unmapped:
- description: 'AI client access: the OAuth server, consent page, connected apps and the MCP endpoint for managing users.'
  paths:
  - api/src/oauth.rs
  - api/src/oauth_http.rs
  - api/src/mcp.rs
  - web/src/admin/pages/OAuthAuthorize.tsx
  - web/src/admin/pages/SettingsConnectedApps.tsx
- description: API tokens for programmatic access and their management pages.
  paths:
  - web/src/admin/pages/ApiTokenList.tsx
  - web/src/admin/pages/ApiTokenNew.tsx
  - web/src/admin/pages/ApiTokenEdit.tsx
- description: Kiosk health check pings to an outside monitor.
  paths:
  - api/src/bin/healthcheck-lambda.rs
- description: The administrators' command-line inspector and NITC tag loader.
  paths:
  - api/src/bin/cli.rs
  - api/src/bin/load-nitc-tags.rs
- description: Kiosk self-reported diagnostics and the kiosk status dialog.
  paths:
  - api/src/client_info.rs
  - web/src/kiosk/components/KioskStatusDialog.tsx
limitations: []
---

# Coverage
