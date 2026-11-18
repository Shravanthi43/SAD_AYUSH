
# AYUSH Digital Health Platform – Member Responsibilities

**Project:** AYUSH Digital Health Platform

This document defines the responsibilities, scope, included components, technologies and dependencies of all four project members.

---

# Member 1 – Frontend Development

## Scope
Owns the client-side React/Vite application, shared user interface and frontend modules for all AYUSH domains.

## Responsibilities
- Shared React UI and application navigation.
- Patient, Doctor, Clinic and Admin screens.
- Registration and user interface components.
- Frontend modules for Ayurveda, Yoga & Naturopathy, Unani, Siddha and Homoeopathy.
- Common Clinical and Longitudinal Record frontend modules.
- Frontend API client and integration with backend APIs.
- Localization, speech UI and reusable components.
- Aadhaar and face-capture user interface.
- Vite configuration and frontend build setup.
- Public face-recognition model assets.

## Included Components
- Shared Platform frontend.
- Ayurveda frontend modules.
- Yoga & Naturopathy frontend.
- Unani frontend.
- Siddha frontend.
- Homoeopathy frontend.
- Common Clinical frontend.
- Longitudinal Record frontend.
- React application entry point and HTML.
- Vite configuration and public model assets.

## Technologies
- React 19
- Vite 6
- React Router
- JavaScript
- JSX
- CSS
- Face API browser assets

## Setup and Execution
```bash
npm ci
npm run dev
```

Frontend runs at:

`http://localhost:5173`

Build verification:

```bash
npm run build
```

## Dependencies on Other Members
- Member 2 provides backend APIs.
- Member 4 provides the API Gateway and integration services.
- Member 3 manages database persistence used by backend services.

## Integration Notes
The frontend is part of the unified application and requires the integrated backend and API Gateway for API-connected screens. The frontend-only package is not a standalone backend application.

---

# Member 2 – Backend Services

## Scope
Owns the backend business logic and Express service implementations for the AYUSH domains, Shared Platform, Common Clinical and Longitudinal Record.

## Responsibilities
- Shared Platform authentication and registration backend.
- OTP and user-management backend workflows.
- Patient, Doctor and Admin backend routes.
- Aadhaar and face-related backend workflows.
- Ayurveda backend service.
- Yoga & Naturopathy backend service.
- Unani backend service.
- Siddha backend service.
- Homoeopathy backend service.
- Common Clinical backend service.
- Longitudinal Record backend service.
- Shared backend middleware and validation helpers.
- Backend communication with database and integration components.

## Included Components
- Five AYUSH domain backends.
- Common Clinical backend.
- Shared Platform backend.
- Longitudinal Record backend.
- Shared backend helper modules.

## Technologies
- Node.js
- Express.js
- JavaScript
- SQLite through shared database helper
- Backend middleware and validation

## Setup and Execution
```bash
npm ci
npm run check
```

The syntax check verifies JavaScript source files.

## Dependencies on Other Members
- Member 3 provides database helper and database-related components.
- Member 4 provides API Gateway, Event Bus and integration services.
- Member 1 consumes backend APIs through the frontend.

## Integration Notes
Database schemas are currently initialized from backend source files in this project. The backend package is not the complete multi-process application; full end-to-end execution requires Member 4's gateway, Event Bus and integration modules.

---

# Member 3 – Database Design and Management

## Scope
Owns database directories, the SQLite openDb helper, Shared Platform database schema and seed logic, and backend source files that define or initialize service-specific schemas.

## Responsibilities
- SQLite database connection and initialization.
- Shared database helper management.
- Shared Platform database schema and table management.
- Seed logic for development and testing.
- Database ownership and persistence.
- Database isolation across microservices.
- Coordination with backend developers for schema requirements.
- Review of database-related service initialization.

## Included Components
- `libs/common/db.js`
- `shared-platform/backend/db.js`
- `shared-platform/backend/seed.js`
- `api-gateway/database/`
- `event-bus/database/`
- `integrations/database/`
- `longitudinal-record-service/database/`
- `services/ayurveda-service/database/`
- `services/common-clinical-service/database/`
- `services/homoeopathy-service/database/`
- `services/siddha-service/database/`
- `services/unani-service/database/`
- `services/yoga-naturopathy-service/database/`
- Backend source files containing service-specific schema definitions.

## Technologies
- SQLite
- better-sqlite3
- Node.js
- Database initialization and seed logic

## Setup and Execution
Install the full integrated application's dependencies:

```bash
npm install
```

Run seed data when required:

```bash
npm run seed
```

Verify database isolation after integration:

```bash
npm run test:isolation
```

## Dependencies on Other Members
- Member 2 uses the database helper and schema definitions in backend services.
- Member 4 uses shared database functionality for integrations and Event Bus components.
- Member 1 consumes persisted data through backend APIs.

## Integration Notes
The supplied source does not have separate migration or schema files for every service. Several service schemas are embedded in backend server files and/or the shared domain-service builder. Those exact files must be retained because removing them would remove the actual database schema definitions.

This is a database-focused work package, not a standalone database server. Full runtime database tests require the full integrated application's dependencies and services.

---

# Member 4 – API & Integration

## Scope
Owns the API Gateway, Event Bus, Integrations service (including WhatsApp/OCR/voice), shared inter-service integration helpers, project orchestration, tests and root runtime configuration.

## Responsibilities
- API Gateway routing and request handling.
- Token verification and rate limiting.
- Request IDs, CORS and proxy routing.
- Event Bus publish/subscribe delivery and retry handling.
- Integrations backend.
- WhatsApp bot, drivers and language modules.
- WhatsApp OCR reader and voice modules.
- External healthcare status endpoint.
- Shared service routing and configuration.
- Internal HTTP clients and event publishing helpers.
- Root scripts and service process orchestration.
- Project-wide tests and runtime configuration.

## Included Components
- API Gateway backend.
- Event Bus backend.
- Integrations backend.
- WhatsApp integration modules.
- External healthcare integration.
- Shared configuration and event helpers.
- Internal HTTP helper modules.
- Project-wide acceptance and isolation tests.
- Health-check and service orchestration scripts.
- Root `package.json` and `package-lock.json`.
- Environment example configuration.

## Technologies
- Node.js
- Express 4
- API Gateway and reverse proxy
- HTTP inter-service clients
- Event Bus
- WhatsApp integration using optional Baileys dependency
- Tesseract OCR
- Voice processing modules

## Setup and Execution
Configure environment variables using `.env.example`. Never commit `.env` files or credentials.

Install dependencies:

```bash
npm install
```

Start the application:

```bash
npm run dev
```

Health check:

```bash
npm run health
```

Available project checks:

```bash
npm run check
npm test
npm run test:isolation
npm run test:reader
npm run build
```

## Dependencies on Other Members
- Member 2's backend services are required for gateway routing and end-to-end tests.
- Member 3 provides database helper functionality used by Event Bus and Integrations.
- Member 1's frontend is served through Vite and communicates through the API Gateway.

## Integration Notes
The original Member 4 package did not contain an existing GitHub Actions workflow. The CI workflow is maintained separately under `.github/workflows/` in the integration repository.

---

# Overall Project Integration

All four members contribute to one unified AYUSH Digital Health Platform.

| Member | Main Responsibility |
|---|---|
| Member 1 | Frontend Development |
| Member 2 | Backend Services |
| Member 3 | Database Design and Management |
| Member 4 | API Gateway and Integrations |

## Integration Flow

1. Member 1 develops the frontend interface.
2. Member 2 implements backend services and business logic.
3. Member 3 manages database helper functionality, schema and persistence.
4. Member 4 handles API Gateway, Event Bus and external integrations.
5. The frontend communicates with backend services through the API Gateway.
6. Backend services use their assigned database components.
7. Event Bus and integration services support inter-service communication.

## GitHub Branch Strategy

Each member maintains a separate development branch:

- `frontend`
- `backend`
- `database`
- `api-integration`

Member branches are integrated into `api-integration` after resolving conflicts and verifying the changes.

After integration, the complete application is tested before merging into `main`.

## Continuous Integration

GitHub Actions is used to automate project checks whenever changes are pushed to the configured integration branch.

The CI pipeline can include:
- Dependency installation.
- JavaScript syntax checking.
- WhatsApp reader regression testing.
- Frontend build verification.
- Database isolation testing.
- Full acceptance testing.

Full integration tests should run after all required project components are present in the integration branch.
