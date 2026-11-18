
# AYUSH Digital Health Platform – Member Responsibilities

**Project:** AYUSH Digital Health Platform (updated `Ayush_Health.zip`)

This document describes the responsibilities, included files, technologies, setup instructions and integration dependencies of the project members.

---

# Member 1 – Frontend Development

**Scope:** Owns the React/Vite user interface and frontend assets for the unified AYUSH application.

## Responsibilities
- Shared React application shell, navigation, registration, patient/doctor/clinic/admin screens and frontend hooks.
- Frontend modules for Ayurveda, Common Clinical and Longitudinal Record, plus the service-picker registration modules for the other AYUSH systems.
- Frontend API client, localization, speech UI, Aadhaar/face capture UI, styles and reusable components.
- Vite aliases and HTML entry point; browser-side face recognition model assets.

## Included files (original project-relative paths)
- `index.html`
- `longitudinal-record-service/frontend/pages/patient/Timeline.jsx`
- `public/models/face_landmark_68_model-weights_manifest.json`
- `public/models/face_landmark_68_model.bin`
- `public/models/face_recognition_model-weights_manifest.json`
- `public/models/face_recognition_model.bin`
- `public/models/tiny_face_detector_model-weights_manifest.json`
- `public/models/tiny_face_detector_model.bin`
- `scripts/copy-models.js`
- `services/ayurveda-service/frontend/DoctorLayout.jsx`
- `services/ayurveda-service/frontend/index.js`
- `services/ayurveda-service/frontend/pages/Comparison.jsx`
- `services/ayurveda-service/frontend/pages/Dashavidha.jsx`
- `services/ayurveda-service/frontend/pages/Diagnosis.jsx`
- `services/ayurveda-service/frontend/pages/Examination.jsx`
- `services/ayurveda-service/frontend/pages/PrakritiVikriti.jsx`
- `services/ayurveda-service/frontend/pages/Therapy.jsx`
- `services/common-clinical-service/frontend/components/CommonClinical.jsx`
- `services/common-clinical-service/frontend/pages/UploadPrescription.jsx`
- `services/common-clinical-service/frontend/pages/patient/AddRecord.jsx`
- `services/common-clinical-service/frontend/pages/patient/Medicines.jsx`
- `services/common-clinical-service/frontend/pages/patient/Uploads.jsx`
- `services/homoeopathy-service/frontend/index.js`
- `services/siddha-service/frontend/index.js`
- `services/unani-service/frontend/index.js`
- `services/yoga-naturopathy-service/frontend/index.js`
- `shared-platform/frontend/App.jsx`
- `shared-platform/frontend/api/client.js`
- `shared-platform/frontend/components/AadhaarFetch.jsx`
- `shared-platform/frontend/components/FaceCapture.jsx`
- `shared-platform/frontend/components/Field.jsx`
- `shared-platform/frontend/components/FormPage.jsx`
- `shared-platform/frontend/components/LangSwitch.jsx`
- `shared-platform/frontend/components/OtpBox.jsx`
- `shared-platform/frontend/components/PatientShell.jsx`
- `shared-platform/frontend/components/RoleRegister.jsx`
- `shared-platform/frontend/components/Steps.jsx`
- `shared-platform/frontend/components/TopBar.jsx`
- `shared-platform/frontend/components/VoiceMic.jsx`
- `shared-platform/frontend/constants/options.js`
- `shared-platform/frontend/domains.js`
- `shared-platform/frontend/hooks/useDraft.js`
- `shared-platform/frontend/hooks/usePrefill.js`
- `shared-platform/frontend/hooks/useSummary.js`
- `shared-platform/frontend/i18n/dict.js`
- `shared-platform/frontend/i18n/domTranslate.js`
- `shared-platform/frontend/i18n/index.jsx`
- `shared-platform/frontend/index.css`
- `shared-platform/frontend/main.jsx`
- `shared-platform/frontend/pages/Assistant.jsx`
- `shared-platform/frontend/pages/DomainConsultation.jsx`
- `shared-platform/frontend/pages/Landing.jsx`
- `shared-platform/frontend/pages/Me.jsx`
- `shared-platform/frontend/pages/admin/Dashboard.jsx`
- `shared-platform/frontend/pages/clinic/Dashboard.jsx`
- `shared-platform/frontend/pages/doctor/FindPatient.jsx`
- `shared-platform/frontend/pages/patient/Privacy.jsx`
- `shared-platform/frontend/pages/patient/Profile.jsx`
- `shared-platform/frontend/pages/patient/Services.jsx`
- `shared-platform/frontend/pages/register/Admin.jsx`
- `shared-platform/frontend/pages/register/Choose.jsx`
- `shared-platform/frontend/pages/register/Clinic.jsx`
- `shared-platform/frontend/pages/register/Doctor.jsx`
- `shared-platform/frontend/pages/register/Patient.jsx`
- `shared-platform/frontend/utils/aadhaar.js`
- `shared-platform/frontend/utils/session.js`
- `shared-platform/frontend/utils/time.js`
- `shared-platform/frontend/voice/speech.js`
- `vite.config.js`

## Technologies / components observed
- React 19
- Vite 6
- React Router
- JSX/CSS
- @vladmandic/face-api browser model assets
- Frontend API client and browser speech utilities

## Setup and execution
- Start from the complete repository's main branch, not an empty folder.
- At the repository root run `npm install` (root package.json is shared and retained from the base project).
- Run `npm run dev` to start all services and Vite; open `http://localhost:5173`.
- Do not replace the root package.json or package-lock.json with a frontend-only manifest.

## Dependencies on other members
- Member 4's API Gateway must be running on port 5000 for API calls; Vite proxies `/v1`, `/api` and WhatsApp paths to it.
- Member 2's backend services must be available behind the gateway for data-backed screens.
- Member 4 owns root package.json/package-lock.json and environment/runtime orchestration.

## Integration notes
This package is a frontend work package, not a standalone application. The frontend folders from all services are compiled into one React/Vite site. Face model binaries are included under `public/models`.

---

# Member 2 – Backend Services

**Scope:** Owns the business logic and Express service implementations for the Shared Platform, five AYUSH domains, Common Clinical and Longitudinal Record.

## Responsibilities
- Shared Platform authentication, OTP, registration, patient/doctor/admin routes, face and Aadhaar backend workflows.
- Five AYUSH domain service server implementations and common domain-service plumbing.
- Common Clinical and Longitudinal Record backend APIs and service business logic.
- Shared backend middleware and validation/security helpers included in this package.

## Included files (original project-relative paths)
- `libs/common/domain-service.js`
- `libs/common/http.js`
- `libs/common/security.js`
- `libs/common/validate.js`
- `longitudinal-record-service/backend/server.js`
- `services/ayurveda-service/backend/server.js`
- `services/common-clinical-service/backend/server.js`
- `services/homoeopathy-service/backend/server.js`
- `services/siddha-service/backend/server.js`
- `services/unani-service/backend/server.js`
- `services/yoga-naturopathy-service/backend/server.js`
- `shared-platform/backend/aadhaar.js`
- `shared-platform/backend/context.js`
- `shared-platform/backend/face.js`
- `shared-platform/backend/otp.js`
- `shared-platform/backend/routes-admin.js`
- `shared-platform/backend/routes-auth.js`
- `shared-platform/backend/routes-internal.js`
- `shared-platform/backend/routes-patient.js`
- `shared-platform/backend/routes-registration.js`
- `shared-platform/backend/server.js`

## Technologies / components observed
- Node.js
- Express 4
- SQLite via better-sqlite3 (through shared DB helper)
- Shared service authentication/validation middleware
- AYUSH domain-service backend pattern

## Setup and execution
- Start from the complete repository's main branch so all shared libraries and root configuration are present.
- At the repository root run `npm install` and configure `.env` from `.env.example` (do not commit `.env` or secrets).
- Run `npm run dev` to launch the full service set; use `npm run health` to inspect service health.
- Run `npm run check` for the repository-wide syntax check.

## Dependencies on other members
- Member 3 provides `libs/common/db.js` and the Shared Platform database initializer/seed files.
- Member 4 provides `libs/common/config.js`, `events.js` and `internal.js`, plus the API Gateway, Integrations service and Event Bus.
- Member 1's frontend calls these APIs through Member 4's API Gateway.

## Integration notes
The backend service source files remain in their original service folders. Several service schemas are initialized in their backend server files or in `libs/common/domain-service.js`; do not move those definitions without coordinating with Member 3 because that would change the existing architecture.

---

# Member 4 – API & Integration

**Scope:** Owns the API Gateway, Event Bus, Integrations service (including WhatsApp/OCR/voice), shared inter-service integration helpers, project orchestration, tests and root runtime configuration.

## Responsibilities
- API Gateway routing, token verification, rate limiting, request IDs, CORS and proxy routing.
- Event Bus publish/subscribe delivery and retry handling.
- Integrations backend, WhatsApp bot/drivers/language/reader/voice modules, OCR language data and external-healthcare status endpoint.
- Shared service routing/configuration, internal HTTP clients and event publishing helpers.
- Root scripts, service process orchestration, project-wide tests, documentation and runtime package/environment configuration.

## Included files (original project-relative paths)
- `.env.example`
- `.gitignore`
- `README.md`
- `api-gateway/backend/server.js`
- `api-gateway/frontend/README.md`
- `docs/ACCEPTANCE-EVIDENCE.md`
- `docs/ARCHITECTURE.md`
- `docs/LIMITATIONS.md`
- `docs/OCR-READER-FIX.md`
- `event-bus/backend/server.js`
- `integrations/backend/server.js`
- `integrations/external-healthcare/status.js`
- `integrations/tessdata/eng.traineddata`
- `integrations/whatsapp/bot.js`
- `integrations/whatsapp/drivers.js`
- `integrations/whatsapp/i18n.js`
- `integrations/whatsapp/reader.js`
- `integrations/whatsapp/voice.js`
- `libs/common/config.js`
- `libs/common/events.js`
- `libs/common/internal.js`
- `package-lock.json`
- `package.json`
- `scripts/acceptance-test.js`
- `scripts/check-syntax.js`
- `scripts/dev-all.js`
- `scripts/health.js`
- `scripts/isolation-test.js`
- `scripts/reader-test.js`
- `scripts/services.js`

## Technologies / components observed
- Node.js
- Express 4
- API Gateway / reverse proxy
- HTTP inter-service clients
- Event Bus (durable publish/subscribe)
- WhatsApp integration (Baileys optional dependency)
- Tesseract OCR / voice processing modules
- Project test and orchestration scripts

## Setup and execution
- Start from the complete repository's main branch.
- Copy `.env.example` to `.env` and set required secrets/provider settings locally; never commit `.env` or credentials.
- Run `npm install`, then `npm run dev` to launch the Event Bus, Gateway, backend services, Integrations and Vite.
- Run `npm run health`, `npm test`, `npm run test:isolation`, `npm run test:reader`, `npm run check` and `npm run build` as appropriate.

## Dependencies on other members
- Member 2's backend services must be running for gateway routing, internal service calls and end-to-end tests.
- Member 3's database helper is used by Event Bus and Integrations and must remain available.
- Member 1's frontend is served through Vite in development and by the Gateway after a production build.

## Integration notes
The uploaded project has no existing `.github/workflows` CI workflow in the original package. This package includes project test/orchestration scripts and the API/integration code. GitHub Actions CI configuration has been added separately in this repository.

---

# GitHub Branch Usage

Each member branch should be created from the same complete, working project baseline in `main`.

Extract each member ZIP at the repository root so the original paths overlay the baseline. Do not create a new empty repository from an individual ZIP alone; each package intentionally contains only the files assigned to that member.

After testing, merge each member branch into the integration branch and verify the complete application before merging the integrated result into `main`.
