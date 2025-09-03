---
mode: 'agent'
model: gpt-4
description: 'Build an Angular 16 Participant Admin (CRUD + List + Dashboard) that consumes a Laravel REST API with API-key auth'
---

Goal
Create an Angular 16 web app called **Participant Admin** that manages "participants" (trainees) via a Laravel 8 API hosted at `https://api.hereandnowai.com/public/api`. Implement a clean admin UI with: (1) Create/Edit form, (2) List view with search/sort/pagination, (3) Dashboard summarizing collected data with charts.

Backend API (already exists)
- Base URL: `https://api.hereandnowai.com/public/api`
- Resource: `participants`
- Endpoints:
  - GET `/participants`           → list all
  - GET `/participants/{id}`      → get one
  - POST `/participants`          → create
  - PUT `/participants/{id}`      → update
  - DELETE `/participants/{id}`   → delete
- Auth: Send API key in header `X-API-KEY: <value>` (make header name configurable).
- JSON fields:
  - name (string, required)
  - whatsapp (string)
  - email (string, email)
  - linkedin (string, url)
  - github_id (string)
  - python_skill (int 1-10)
  - angular_skill (int 1-10)
  - javascript_skill (int 1-10)
  - html_skill (int 1-10)
  - css_skill (int 1-10)
  - java_skill (int 1-10)
  - outcome (string)
  - id, created_at, updated_at (server-side)

Tech/Architecture
1) Angular 16 + TypeScript, module-based (not standalone API).
2) Use Angular Router with 3 main routes:
   - `/participants` (List)
   - `/participants/new` (Create)
   - `/participants/:id` (Edit/Detail)
   - `/dashboard` (Dashboard)
   - Redirect unknown routes to `/participants`.
3) Use **Reactive Forms** with validation and helpful error messages.
4) Use **HttpClient** with an **HTTP interceptor** that injects the API key header and `Accept: application/json`.
5) Styling: keep it clean, responsive; use Angular Material OR a minimal Tailwind setup (choose one and wire it up).
6) Charts: use `chart.js` via `ng2-charts` for the dashboard (bar/pie/radar as appropriate).
7) Code quality: strong typing via interfaces, services, and clear separation of concerns.

Data model
Create an interface `Participant` with the fields listed above.

Environment & Config
- Create `src/environments/environment.ts` and `.prod.ts` with:
  - `apiBaseUrl: 'https://api.hereandnowai.com/public/api'`
  - `apiKeyHeaderName: 'X-API-KEY'`
  - `apiKeyValue: 'REPLACE_WITH_REAL_KEY'`
- The interceptor must read from `environment` so we can switch keys/URLs without touching code.
- Provide a README section describing where to set the API URL and key.

Features (Detailed)
1) List View (`/participants`)
   - Table view with columns: Name, Email, WhatsApp, LinkedIn, GitHub, Created At, Actions (View/Edit/Delete).
   - Client-side search (by name/email/github_id) and sort (at least by Created At and Name).
   - Pagination (client-side is fine; keep the code simple and well-commented to swap to server-side later).
   - “Add Participant” button linking to `/participants/new`.
   - Delete action with confirmation dialog; on success, refresh list and show a snack-bar/toast.

2) Create/Edit Form (`/participants/new`, `/participants/:id`)
   - Reactive form with controls and validators:
     - name: required, maxLength(255)
     - whatsapp: optional, pattern for digits/plus/minus/spaces
     - email: optional, email
     - linkedin: optional, url pattern
     - github_id: optional
     - python_skill, angular_skill, javascript_skill, html_skill, css_skill, java_skill: optional, integer 1..10 (use select or slider)
     - outcome: textarea
   - On submit:
     - If new → POST, else → PUT
     - Show success/failure messages
     - Navigate back to list after success
   - “Cancel” returns to the list.
   - When editing, prefill with GET `/participants/:id`.

3) Dashboard (`/dashboard`)
   - Fetch all participants and compute:
     - Count total participants
     - Average of each skill (python, angular, javascript, html, css, java)
     - Distribution charts:
       - Bar chart for average skills
       - Pie or doughnut chart showing proportions of skill levels (e.g., 1–3, 4–6, 7–10) aggregated across one chosen skill (e.g., Angular)
       - Optional radar chart comparing average skills
   - Show top-line KPI cards: Total Participants, Avg Angular, Avg JS, Avg Python (etc.).
   - Handle empty-state gracefully.

Services & Interceptor
- `participants.service.ts`:
  - Methods: `list()`, `get(id)`, `create(dto)`, `update(id, dto)`, `remove(id)`
  - Strong typing for inputs/outputs with `Participant` interface.
  - Centralized error handling (map to user-friendly messages).
- `auth.interceptor.ts`:
  - Reads from `environment.apiKeyHeaderName` and `environment.apiKeyValue`.
  - Adds headers to every outgoing request:
    - `Content-Type: application/json`
    - `Accept: application/json`
    - `<apiKeyHeaderName>: <apiKeyValue>`

Modules/Files to Generate (full code, ready to run)
- `app.module.ts`, `app-routing.module.ts`
- `environments/environment.ts`, `environments/environment.prod.ts`
- `models/participant.model.ts`
- `services/participants.service.ts`
- `interceptors/auth.interceptor.ts`
- Components:
  - `participants-list/participants-list.component.ts|html|css`
  - `participant-form/participant-form.component.ts|html|css` (used for both new/edit)
  - `dashboard/dashboard.component.ts|html|css`
  - `layout/shell.component.ts|html|css` (optional) with a top nav (Participants, Dashboard)
- If using Angular Material, include a `material.module.ts` to bundle imports.
- Provide minimal, clean CSS for responsive layout.

UX Details
- Global toolbar with app title “Participant Admin”, nav links to List and Dashboard.
- Use mat-table (or a simple HTML table) with sticky header and responsive behavior.
- Form uses mat-form-field (or clean inputs) with inline validation hints.
- Snack-bar/Toast on create/update/delete success/failure.

README (top-level or in `README.md`)
- How to set `environment.ts` for API URL and API key.
- How to install and run:
  - `npm install`
  - `ng serve`
- Notes on required Node/Angular versions.
- Notes on switching to server-side pagination (optional section).

Acceptance Criteria
- App builds and runs on Angular 16.
- All CRUD operations succeed against the Laravel API when a valid API key is configured.
- List supports search, sort, and pagination.
- Form validates inputs and shows helpful messages.
- Dashboard shows KPIs and charts derived from live data.
- Interceptor reliably injects the API key on all requests.
- Clean structure, comments explaining key parts (forms, service, interceptor, charts).

Assumptions/Instructions for the Agent
- If any package is needed (Angular Material, ng2-charts, chart.js, Tailwind), install and wire it up.
- Prefer simple, well-commented implementations. Where trade-offs exist, choose clarity over cleverness.
- Do not include server code; this app consumes the existing Laravel API only.
- If the API returns fields not present in the model, ignore them gracefully.

Output
Generate the full project code for the files listed above, with complete implementations, comments, and minimal styling. 
