# Partnr — Multi-Tenant SaaS Platform

![Status](https://img.shields.io/badge/status-pending-orange) ![Docker](https://img.shields.io/badge/docker-required-blue) ![License](https://img.shields.io/badge/license-MIT-lightgrey)

Partner / Product: Partnr

Author: Lakshmi Prasanna Duvvu

Project: Build Multi-Tenant SaaS Platform with Project & Task Management (Mandatory Task)

Deadline: 3 Jan 2026, 04:59 PM

Time Remaining: 1d (as of last update)

## Overview

This repository contains a dockerized, multi-tenant SaaS application implementing project and task management. The system demonstrates tenant isolation, role-based access, JWT auth, containerized deployment, automatic DB migrations, and seed data required for automated evaluation.

This README documents submission requirements, run instructions, seed credentials, and the evaluation checklist.

## Quick Links

- Project root: [README.md](README.md)
- API docs: [docs/API.md](docs/API.md)
- Architecture: [docs/architecture.md](docs/architecture.md)
- Tech spec: [docs/technical-spec.md](docs/technical-spec.md)
- Submission manifest: [submission.json](submission.json)

## How to run (Docker - REQUIRED)

Requirements: Docker Desktop (or equivalent) and Docker Compose.

1. From project root run:

```bash
docker-compose up --build -d
```

2. Confirm services are healthy:

```bash
docker-compose ps
docker-compose logs -f backend
```

3. Health checks:

- Frontend: http://localhost:3000
- Backend health check: http://localhost:5000/api/health

4. Stop and cleanup:

```bash
docker-compose down -v
```

## Local development (optional)

Run services individually for development if needed:

Backend:

```bash
cd backend
npm install
npm run dev
```

Frontend:

```bash
cd frontend
npm install
npm run dev
```

## Submission Requirements (full)

Follow the assignment checklist EXACTLY. The evaluator will verify each item.

1. GitHub Repository (Public)

   - All backend and frontend source code
   - Migration SQL files and `src/scripts/migrate.js`
   - Seed script and seed data (`src/scripts/seed.js`)
   - Minimum 30 meaningful commits on GitHub

2. Dockerized Application (MANDATORY)

   - `docker-compose.yml` at repository root defines these services and names:
     - database (Postgres 15) exposing port `5432:5432`
     - backend exposing port `5000:5000` and named `backend`
     - frontend exposing port `3000:3000` and named `frontend`
   - Backend and Frontend Dockerfiles using proper multi-stage builds
   - Database persistence via Docker named volume
   - `docker-compose up -d` must start all services automatically

3. Database Initialization (MANDATORY - Automatic Only)

   - Migrations MUST run automatically when backend starts
   - Seed data MUST load automatically after migrations
   - Seed must include at minimum:
     - One `super_admin` user
     - One tenant with `tenant_admin`
     - At least one regular user per tenant
     - At least one project per tenant
     - At least one task per project
   - All seed credentials MUST be documented in `submission.json` under `testCredentials`.

4. Documentation

   - `README.md` with quick-start, Docker setup and demo video link
   - `docs/` must include: `API.md`, `architecture.md`, `technical-spec.md`, `PRD.md`, `research.md` and images for system architecture and DB ERD

5. Demo Video

   - 5–12 minutes uploaded to YouTube (Unlisted/Public)
   - Include link in this README and submission form

6. submission.json (MANDATORY)
   - Present in repository root and include `testCredentials` for automated evaluation

## Evaluation Focus

- Data isolation between tenants
- Authentication and RBAC correctness
- All API endpoints functional and secured (19 endpoints expected)
- Frontend pages and role-based UI visibility
- Docker configuration and containerization (MANDATORY)
- DB initialization and seed data loading
- Health check endpoint functionality
- Documentation completeness and quality

## Seeded Test Credentials (example)

After running the stack the seeded demo accounts (already included by the seed script) can be used to test the app. Ensure these exact credentials are also placed in `submission.json`.

- Tenant Admin (Demo Company)

  - Workspace / Subdomain: demo
  - Email: admin@demo.com
  - Password: Demo@123

- Regular User (Demo Company)

  - Workspace / Subdomain: demo
  - Email: user1@demo.com
  - Password: User@123

- Super Admin (system-wide)
  - Workspace: (leave empty)
  - Email: superadmin@system.com
  - Password: Admin@123

## Checklist before final submission

- [ ] `docker-compose up -d` starts all three services and DB becomes `Healthy`
- [ ] Health endpoint returns `ok`
- [ ] `submission.json` present with correct `testCredentials`
- [ ] docs/ contains required documents and diagrams
- [ ] Demo video uploaded and link included in README
- [ ] 30+ meaningful commits exist on GitHub

## Contact & Legal

Partnr © 2025-26

About Us | Contact Us | Privacy Policy | Terms and Conditions

Report Issue: open an issue on the GitHub repository

If you'd like me to insert the demo video link, embed images, or update `submission.json` contents, tell me what to add and I'll patch the file.
