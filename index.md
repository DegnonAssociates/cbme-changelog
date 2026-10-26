---
title: Changelog
---

# Changelog

Reverse chronological record of app features, updates, and bugfixes since creation.

Entries before 2026-08-12 were reconstructed from the local git history.

## 2026-10-26

- Explain expired sessions on the login screen and ask users to sign in again. Protected requests with invalid session cookies preserve the requested page for return after login; first-time visitors keep the normal login flow.

## 2026-10-24

- Fixed staging's initial program-selection race: wait for the saved selection to load and attempt automatic fallback only once, preventing repeated page reloads while preserving manual program-switch warnings and production behavior.
- Shortened staging EPA Import guidance by placing the file picker first and keeping detailed column, formatting, and EPA-scale rules in expandable help. Added explicit not-imported, checked, importing, and saved states.
- Added staging-only unsaved-work warnings for assessment corrections/previews, account and administration edits, and trainee setup files. Canceled navigation preserves edits, successful saves release protection, and failed program changes restore warnings; production behavior and import payloads remain unchanged.
- Added staging Results filename search, assessment season/year filters, newest-first ordering, and ten assessments per page, with clear matching counts and no-match recovery.
- Added trainee name/ID search and PGY filters across staging comparison and detail views. Report-type navigation preserves filters and the selected trainee, including when that trainee has no results in one report.
- Matched report-page spreadsheet, PDF, and ZIP download buttons to the shared staging treatment while preserving complete-assessment downloads, report values, and production behavior.

## 2026-10-17

- Render staging administration per request, keeping authenticated admin pages out of build-time prerendering. The production layout retains its existing rendering path.

- Wrapped the staging form context in a named client component to keep its server-rendered layout boundary explicit.

- Applied the approved grouped editor to all nine staging admin add/edit forms, with record headings, related field sections, responsive layouts, and explicit Cancel/Save actions.
- Added linked field validation, focus on error summaries, retained edits after failed saves, and pending/empty member states. Staging framework assignment edits now show their stored selections. Existing server actions, hidden identifiers, callbacks, authorization, and production layouts remain unchanged.

## 2026-10-16

- Added a staging-only Administration home grouping programs and people, activity and exports, and reference data, with all ten existing admin destinations available.
- Moved staging Administration into its own sidebar section below Results and added administration context and return navigation on admin pages.
- Added staging admin table search, active/inactive filters where applicable, matching counts, and clear empty/error states while preserving existing actions, server-side roster/metrics filters, Global Admin permissions, and production presentation.

## 2026-10-15

- Send password-reset email directly through Amazon SES using dedicated `SES_*` settings and the existing CBME AWS user, removing the AWS-API mail relay dependency.
- Preserve the sender, HTML and plain-text content, and password-reset response behavior; bound each send to ten seconds and disable SDK retries to avoid duplicate sends after uncertain outcomes.
- Document Railway credential references and removal of `AWS_MAIL_TOKEN` after deployment. The report worker continues to use S3 directly and requires no email settings.

## 2026-10-14

- Unified staging spreadsheet, PDF, and ZIP download buttons with aligned format labels and a darker green hover state; replaced button-link hover underlines with blue/teal background shading while preserving ordinary text-link underlines, keyboard focus, and production styling.
- Removed duplicate assessment history from staging EPA Import and replaced it with a View Results link; history, report status, and downloads remain in Results.
- Routed staging partial-success imports to Results with saved-data reassurance and no-repeat-upload guidance, including refresh/support actions when history is temporarily empty. Production's import history and recovery destination are unchanged.
- Applied the approved blue and teal styling to staging: a cool canvas, clearer selected-program navigation, and task rows with an emphasized assessment upload action.
- Added matching light and dark palettes, keyboard focus treatments, and responsive dashboard spacing. The exact staging environment gate keeps production styling unchanged; task permissions, guidance, imports, and report calculations are preserved.
- Kept the staging mobile program dropdown within the sidebar's modal handling so dismissing nested menus does not leave the page unclickable.
- Made Upload assessments match the other dashboard task rows, using a circular arrow and highlighting only on hover instead of a permanent blue row and button treatment.
- Extended the staging blue and teal design to trainee setup, assessment uploads/history, report details, settings, and shared admin/account form elements, with consistent headings, panels, fields, buttons, contained tables, and responsive dialog styling. Existing actions, validations, report values, and production presentation are preserved.

## 2026-10-13

- Added an authenticated staging-only encrypted LEARN ID generator using the owner's supplied derivation rules and public RSA key, with a local template and an XLSX download accepted by the trainee importer.
- Kept birthdates and SSN/SIN last-four digits out of generated downloads, logs, cookies, database records, and object storage; generation does not create or update trainees.
- Protected saved staging trainee IDs by rejecting regeneration for registered program identifiers/NPI and rechecking new imports in a serializable transaction. Production screens, routing, configuration, and data remain unchanged.
- Bound generator uploads to the configured public app origin so authenticated downloads work behind Railway's HTTPS proxy without trusting forwarded-host headers.

## 2026-10-12

- Added staging-only active navigation and persistent selected-program context across dashboard and administration pages.
- Clarified PDF/ZIP generation states and retry actions, distinguishing saved assessments from downloadable reports; added useful refresh and first-upload actions for empty or unavailable history.
- Simplified staging account settings with inline validation, pending controls, persistent save confirmation, and an explicit re-sign-in step after email changes; bound edits to the authenticated account and preserved confirmation while the session still uses the previous email.
- Added a staging-only searchable trainee roster with program/PGY filters, pagination, explicit empty states, and program-specific setup links; kept trainee dates stable across browser timezones.
- Clarified staging trainee setup with the destination program, required spreadsheet headings, template links, and actionable file/row errors; verified destination access again on submission.
- Added a task-focused staging Start page for trainee management, assessment uploads, and Results, while preserving detailed guidance and production's existing screens.
- Added a staging-only Results destination with assessment history, explicit milestone/readiness links, and assessment downloads.
- Added trainee detail alongside the comparison table, preserving trainee selection when switching report types and showing complete names, registered identifiers, program, and assessment period.
- Corrected staging feedback identity and report context, isolating feedback state when switching trainees to prevent stale lookups from appearing for another trainee.
- Added a staging-only results endpoint with program-access checks; production report views and calculations remain unchanged.

## 2026-10-10

- Made Check spreadsheet the primary staging import action, automatically opening column matching when headers need attention. Kept manual adjustments in a smaller link and preserved column selections across rechecks.
- Simplified staging imports to always read the first tab, removing worksheet selection and extra-tab notices while retaining header-row and column matching controls.
- Highlighted unmatched or duplicate column mappings, unmatched trainees, and cell errors with explicit attention labels; added spacing and small-screen wrapping between spreadsheet action buttons.
- Added staging-only worksheet/header selection, explicit column matching and ignored columns, editable cell-level corrections, and a corrected XLSX download from the validated preview. Confirmation binds these choices and edits to the preview and repeats all validation; original files and production's import flow remain unchanged.
- Added staging-only unmatched trainee resolution with explicit, program-scoped choices and preview-bound confirmation; matching changes only the current upload, never the roster.
- Added assessment-level duplicate detection, opt-in skipping of identical rows, links to earlier imports, and blocking of conflicting ratings. An atomic, per-program database lock rechecks duplicates before saving, including simultaneous confirmations; no schema migration is required.
- Added a staging-only check-and-confirm spreadsheet import: automatic header/table detection, safe formatting normalization, exact cell errors, and a no-write preview with trainee/measurement counts. Confirmation revalidates access and a signed file/user/program-bound preview; R receives the normalized workbook. Production's legacy import path is unchanged.
- Avoided secondary mixed-year/season warnings caused solely by invalid cells, keeping spreadsheet correction messages focused on the source problem.
- Restricted header and season alias lookup to explicit supported entries.
- Kept wide staging preview tables inside their scrollable area instead of expanding the entire page.
- Normalized numeric text PGY cells before persistence, rejected invalid PGY types, and corrected import summaries to count stored measurements rather than spreadsheet rows.
- Added guarded staging-only scheduled input cleanup with separate input credentials; retained the 30-day input retention period and protection for active jobs and report outputs.
- Added isolated staging input/output buckets, program-authorized private downloads, and storage smoke checks with optional synthetic test fixtures; production AWS defaults remain unchanged.
- Added a staging-only private R processor for spreadsheet, PDF, and ZIP generation using the supplied CBME package and model, with authenticated requests, bounded concurrency, timeouts, and isolated job files.
- Added an explicit staging provider switch for imports and background reports; the existing provider remains the default and private routing is rejected outside staging.
- Serialized private-processor exports in the legacy import path to respect its one-job capacity while leaving the existing provider's parallel behavior unchanged.
- Added synthetic local and Railway pre-deploy checks without database or storage writes. Production configuration and deployment remain unchanged.

## 2026-10-06

- Added trainee counts and a program-specific View Trainees page for global admins, accessible from Programs and each institution's program list. The roster shows uploaded program-assigned identifiers, encrypted LEARN IDs, trainee start dates, and stored PGY, with identifier search, PGY filtering, and pagination.
- Moved the EPA template download, trainee setup guidance, spreadsheet requirements, and supervision scale from Instructions to EPA Import, above the upload form.

## 2026-09-30

- Added optional background PDF and ZIP generation so report-service failures do not roll back saved imports or delay report review.
- Added private, immutable report inputs, bounded retries, worker leases and recovery, and report status and retry controls while preserving existing downloads.
- Added an additive Prisma migration, standalone Railway worker commands, and a rollout and maintenance runbook. Background generation remains disabled until explicitly configured.
- Restricted import/report access to authorized program members and removed the nonfunctional legacy PDF retry link.

## 2026-09-22

- Updated Next.js and its ESLint configuration to `15.5.26`.
- Documented local setup, service configuration, validation, and database diagram workflows.
- Added logical database diagrams in Mermaid and DBML formats.

## 2026-08-25

- Updated Next.js and its ESLint configuration to `15.5.24`.

## 2026-08-12

- Added this changelog and organized it in reverse chronological order.
- Expanded available entries with extra context from the commit history and changed files where the history provided enough detail.

## 2026-07-31

- Updated production database handling to reuse the shared Prisma client across bundles, reducing the chance of extra client instances in deployed environments.

## 2026-07-29

- Updated Next.js to `15.5.21`.

## 2026-07-16

- Fixed admin export data reconciliation across program actions, export helpers, export API routes, and related tests.
- Added import validation to prevent invalid learner IDs from being accepted.
- Updated login metrics so all Program Admin users are included in the metrics view.

## 2026-07-06

- Improved Prisma transaction handling in learner and spreadsheet import actions.
- Added shared Prisma error handling support.
- Reverted an earlier Prisma import retry/error-handling approach before replacing it with the transaction-focused implementation.

## 2026-06-17

- Made trainee data visible to Global Admin users in the sidebar.
- Allowed Global Admin users to access and use the trainee data pages.

## 2026-06-12

- Removed the Coolify deployment workflow.

## 2026-06-11

- Updated imports, measurement feedback, practice readiness, recommendation feedback, and related API routes to reuse the shared Prisma client.
- Added or updated tests around the shared Prisma client API route changes.

## 2026-06-09

- Fixed CBME hub redirect URLs in auth and form flows.
- Added explicit NextAuth callback route support.
- Trusted the Railway host for auth callbacks.

## 2026-05-29

- Added a service offline maintenance route.
- Updated middleware and auth configuration to support the offline route.
- Added tests for the service offline behavior.

## 2026-05-19

- Fixed default selections in admin program forms.

## 2026-04-24

- Added Coolify auto-deploy workflow support.

## 2026-04-20

- Normalized email handling across auth, forgot-password, and user action flows.
- Added or updated tests for email handling and forgot-password behavior.

## 2026-03-12

- Added tests for user actions, auth configuration, data access, imports, practice readiness, and recommendations.
- Fixed asynchronous update handling in `addToProgram`.

## 2026-02-28

- Fixed forward-push temporary file output so encrypted Learn IDs are not included.
- Added an intercept/debug route for augmented spreadsheet input.
- Fixed mismatched EPA rating names between database storage and uploads, preventing duplicate augmented rows.
- Fixed PGY defaulting to `1` during trainee upload.
- Fixed `FALL` versus `Fall` mismatches between database values and uploaded data.
- Updated augmented spreadsheet generation to build from the original uploaded file and append generated data.
- Removed temporary PDF augmentation logging after the issue was resolved.

## 2026-02-27

- Fixed historical PDF generation issues in spreadsheet import actions.
- Fixed webpack build errors in the PDF/import helper flow.
- Fixed live server environments that did not provide a `File` constructor.

## 2026-02-25

- Stabilized the unit test suite.
- Added encrypted Learn ID error handling in spreadsheet imports.
- Added initial historical data support to newly generated PDFs.

## 2026-02-24

- Added unit tests for learner imports, spreadsheet imports, user actions, validation schemas, and API export behavior.
- Fixed build errors introduced by the test setup.

## 2026-02-21

- Added a dedicated admin login metrics view separate from the general metrics page.

## 2026-02-20

- Updated export filtering.
- Updated metrics filtering.

## 2026-02-19

- Added the initial admin export section.
- Expanded admin exports into a fuller export feature with API route and helper support.

## 2026-02-17

- Fixed additional linting errors.

## 2026-02-13

- Fixed linting errors across the app.

## 2026-01-27

- Reordered the previous imports table columns by season, import date, and file name.

## 2025-12-05

- Updated the Next.js version.

## 2025-12-01

- Changed trainee import filtering to rely only on encrypted Learn ID.

## 2025-11-15

- Updated display fallbacks for names versus encrypted IDs.

## 2025-11-14

- Added signed terms upload functionality.
- Expanded terms and conditions updates across terms pages, upload forms, actions, and supporting library code.

## 2025-11-10

- Expanded terms and conditions functionality.

## 2025-10-19

- Added terms and conditions checking.
- Added the Prisma migration and supporting terms data model changes.

## 2025-10-02

- Added the initial password reset flow.
- Updated the email sender used for password reset messages.
- Added production configuration for reset links in email.

## 2025-09-24

- Added Program Admin email addresses to the metrics table.

## 2025-09-23

- Updated import rules.

## 2025-09-19

- Replaced fallback import behavior with stricter validation.

## 2025-09-17

- Fixed a bug where EPA data validation could report import success even when no measurements were inserted.

## 2025-09-15

- Updated assessment date parsing to accept both strings and numbers.

## 2025-09-12

- Added more robust import validation error handling so validation issues can be reported directly.

## 2025-09-10

- Added the initial metrics dashboard.
- Added additional metrics after the first dashboard pass.

## 2025-09-08

- Updated feedback text.
- Added faster API endpoints.
- Updated additional instructions text.

## 2025-09-07

- Updated instructions.
- Locked EPA data access until a trainee exists.
- Renamed Program Data wording to EPA Data.

## 2025-09-05

- Removed Learn ID from table display.

## 2025-09-04

- Updated instructions.

## 2025-09-03

- Updated red box text.
- Fixed TypeScript build issues.
- Improved timeout handling for PDF generation from large spreadsheets.

## 2025-09-02

- Added requested trainee listing functionality.
- Added user settings confirmation behavior.

## 2025-08-30

- Improved trainee import error handling.
- Rerouted trainee import for Program Admin users.
- Fixed production handling for Zod file validation.
- Added default program selection.
- Enabled default program context behavior.

## 2025-08-29

- Updated user-facing text.
- Added the program combo box to import/admin flows.
- Added a Program tab for Program Admin users.
- Fixed trainee import behavior.

## 2025-08-27

- Added the trainee import confirmation page.
- Added the initial program combo box with placeholder data.
- Made program selection required.

## 2025-08-26

- Updated app text.
- Updated first name and last name display behavior across affected tables.
- Fixed TypeScript build issues.

## 2025-08-22

- Updated validations for learner and spreadsheet imports.
- Fixed TypeScript build errors.

## 2025-08-19

- Renamed learner-facing data model and UI language toward trainee terminology.
- Updated trainee import, program, specialty, and admin form flows.
- Fixed a TypeScript build issue.

## 2025-08-15

- Fixed production spreadsheet upload behavior across import actions, import forms, review forms, and the imports API route.
- Restored API availability after upload changes.
- Added learner fields to the Prisma schema and updated related learner import paths.
- Fixed a TypeScript build issue.

## 2025-08-14

- Fixed TypeScript and ESLint build errors.
- Removed dummy data from affected pages and forms.

## 2025-08-13

- Updated dashboard, feedback modal, measurement feedback modal, previous import, and S3-related text.

## 2025-08-05

- Added learner import functionality with server action, admin import page, form, and validation schema support.

## 2025-07-31

- Added the `MeasurementFeedback` table.
- Added measurement feedback API support and readiness feedback modal behavior.
- Added learner import buttons to admin/program navigation.

## 2025-07-30

- Updated AWS/S3 upload handling for imports.
- Added PDF download support for imported spreadsheet outputs.

## 2025-07-29

- Updated button styling across admin pages, forms, previous import UI, feedback modal, and navigation controls.

## 2025-07-28

- Added practice readiness functionality, including API route, dashboard page, and display component.
- Added ordering for data point headers in practice readiness and recommendations views.
- Added the import-data instructions page and connected it from the dashboard/sidebar.
- Added file upload table support through Prisma migration and schema updates.

## 2025-07-25

- Updated admin buttons and forms to support dark mode styling.
- Added recommendation feedback learner linkage in the Prisma schema.

## 2025-07-22

- Fixed TypeScript errors.
- Added the Leave Feedback button and feedback modal.
- Added processed file storage and cleanup/debug route support for import workflows.

## 2025-06-16

- Fixed a measurement error in spreadsheet import processing.

## 2025-04-22

- Connected recommendations to real data through recommendations/imports API routes and recommendation display components.
- Updated seed data used by recommendation flows.
- Fixed linting errors that blocked Coolify builds.

## 2025-04-17

- Added the database seed script.
- Added Prisma migrations for Learn ID updates and seeding support.
- Updated ERD output and related import/recommendation code for the seeded schema.

## 2025-04-09

- Moved form UI code from `app/ui` to `components/ui/forms`.
- Updated pages to import forms from the new component location.
- Updated generated ERD/dist artifacts.

## 2025-04-04

- Added recommendations navigation and dashboard recommendations page.
- Added the previous imports table.
- Added program display/context components and program selector support.

## 2025-03-26

- Added comments to the Prisma schema.
- Added specialty competency framework admin actions, pages, forms, and sidebar access.

## 2025-03-12

- Added an upload proof of concept with dashboard review-upload flow, review form, validation updates, and import action changes.
- Updated admin edit pages and forms touched by the upload proof of concept.

## 2025-03-07

- Continued admin feature development for institution programs, program members, add-member/add-program forms, breadcrumbs, alerts, and notifications.
- Fixed a sidebar error when no session was present.

## 2025-03-04

- Expanded admin features for competency frameworks, competency items, measurement periods, programs, specialties, and related admin forms.
- Updated Prisma schema and ERD for the expanded admin domain.

## 2025-02-28

- Added programs to the navigation menu.

## 2025-02-27

- Fixed Coolify build issues related to NextAuth.
- Fixed TypeScript issues blocking Coolify builds in auth, dashboard, program, and import paths.

## 2025-02-26

- Added schema support for processing Excel spreadsheet uploads.
- Added dashboard review and confirmation flow support for uploads.
- Added upload success page support.

## 2025-02-21

- Updated work-in-progress dashboard and program page behavior.

## 2025-02-10

- Added spreadsheet upload access from the main dashboard.
- Added the first spreadsheet import action and upload form.

## 2025-02-04

- Restructured admin routes and added admin endpoints for institutions, programs, specialties, and users.
- Added forms and actions for institution, program, specialty, and user management.
- Added the user settings page with edit-user form support.

## 2025-02-03

- Added initial authorization support with auth configuration, middleware, login/new-user pages, data access helpers, and sidebar integration.
- Added the APPD logo asset and initial shared UI components.

## 2025-01-27

- Added the initial Next.js application scaffold from Create Next App.
