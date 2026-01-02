# SaaS Manager — Professional Multi-Tenant Platform

A containerized project & task management platform built with a strict multi-tenant architecture. This README focuses on a concise, professional quick-start and project overview.

![Status](https://img.shields.io/badge/status-stable-green) ![Docker](https://img.shields.io/badge/docker-ready-blue) ![License](https://img.shields.io/badge/license-MIT-lightgrey)

---

## Quick Start

Prerequisites: Docker Desktop and Git.

1. Clone the repository:

```bash
git clone https://github.com/sunil-polupalli/saas-platform.git
cd saas-platform
```

2. Build and run the system (backend, db, frontend):

```bash
docker-compose up --build
```

3. Run DB migrations and seed (inside backend container):

```bash
docker-compose exec backend npm run migrate
docker-compose exec backend npm run seed
```

4. Open the frontend: http://localhost:3000 — backend API: http://localhost:5000/api

5. Stop and cleanup:

```bash
docker-compose down -v
```

---

## Overview

- Frontend: React + Vite + Tailwind
- Backend: Node.js + Express + Sequelize
- DB: PostgreSQL 15 (containerized)

See `docs/` for architecture and API details.

---

## Development (local)

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

---

## Testing & CI

Recommended:

- Backend: Jest + SuperTest (use a dedicated test DB)
- Frontend: Vitest + React Testing Library (mock API calls)

Add CI workflow to run migrations and tests on pull requests.

---

## Seeded Test Accounts

Use the seeded demo accounts after running the seed script.

- Tenant Admin: `admin@demo.com` / `Demo@123` (subdomain: `demo`)
- Regular User: `user1@demo.com` / `User@123`
- Super Admin: `superadmin@system.com` / `Admin@123`

---

If you'd like, I can add a small screenshot, CI workflow, or scaffold the frontend theme tokens to make branding configurable.
**1. Clone the Repository**
