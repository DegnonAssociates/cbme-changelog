# Changelog

Reverse chronological record of app features, updates, and bugfixes since creation.

Entries before 2026-08-12 were reconstructed from the local git history.

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
