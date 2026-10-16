# ByWay — Online Learning Management System

**A collaborative Huma-volve internship project** built for three types of users: learners, instructors, and administrators.

ByWay is a multi-role e-learning application developed with **React, TypeScript, and Vite**, with a separate **Laravel/MySQL REST API**. It brings together course discovery, course and lesson management, reviews, payment-related workflows, instructor revenue insights, and administrative reporting.

> **Project status (October 2026):** The original Laravel API deployment is no longer hosted. The front-end source remains available, but API-dependent flows need a locally running backend or a new deployment. This repository is **not currently advertised as a fully functional public demo**. Payment providers, email delivery, and social sign-in may also require separate credentials and configuration.

## Repository links

- **Front-end (this repository):** [MohammedNasr51/round-5-front-ByWay](https://github.com/MohammedNasr51/round-5-front-ByWay)
- **Original team repository:** [Huma-volve/round-5-front-ByWay](https://github.com/Huma-volve/round-5-front-ByWay)
- **Related Laravel backend:** [Huma-volve/round5-byway](https://github.com/Huma-volve/round5-byway)
- **My front-end contributions:** [Commits by MohammedNasr51](https://github.com/Huma-volve/round-5-front-ByWay/commits?author=MohammedNasr51)

## Why we built it

The goal was to build a realistic learning platform with connected experiences for:

- **Learners:** browse courses, view details and reviews, manage favorites and a cart, access enrolled courses, and follow learning progress.
- **Instructors:** manage profiles, courses, lessons, reviews, revenue information, and withdrawal requests.
- **Administrators:** manage users and courses, review platform activity, configure settings, and inspect financial and analytical dashboards.

The work was completed collaboratively during the Huma-volve internship. Features listed below describe the **team's application**, not work performed by one person alone.

## My role — Mohamed Nasr

**Front-End Developer | Huma-volve Internship | Team project**

I contributed to the React/TypeScript front end, focusing on instructor-facing features, API integration, application structure, and localization. My documented contributions include:

- **Instructor course and lesson management:** integrated REST endpoints for course and lesson workflows; improved pagination, loading states, error handling, and course-management UI.
- **Reviews and profiles:** developed/refined instructor review displays and profile interactions, including paginated reviews, image handling, validation types, and loading skeletons.
- **Revenue and payment interfaces:** contributed instructor revenue charts, withdrawal-request flows, and payment-related API/UI integration.
- **Server-state management:** applied **TanStack Query** for data fetching, mutations, cache invalidation, and optimistic updates with rollback handling in selected course and lesson operations.
- **Shared API infrastructure:** refactored requests around a reusable **Axios instance** with authentication-token attachment and API-error handling.
- **Internationalization:** added and improved **Arabic/English translations**, language switching, and **RTL-aware** layouts and UI behavior.
- **Client-side navigation and maintainability:** contributed role-aware route guards, reusable pagination/components, responsive UI adjustments, and code cleanup.

**Selected evidence:**

- [PR #28 — Instructor/learner profile improvements, reviews, skeletons, localization](https://github.com/Huma-volve/round-5-front-ByWay/pull/28)
- [PR #26 — Centralized API calls and cleanup](https://github.com/Huma-volve/round-5-front-ByWay/pull/26)
- [PR #2 — Instructor reviews, breadcrumbs, localization](https://github.com/Huma-volve/round-5-front-ByWay/pull/2)
- [Full contribution history](https://github.com/Huma-volve/round-5-front-ByWay/commits?author=MohammedNasr51)

> **Scope clarification:** The backend is an associated **team-built Laravel service**. My role described here is **front-end development and integration with its APIs**, not sole ownership or authorship of the Laravel backend, entire admin panel, authentication service, or all learner features.

## Application capabilities

| Area | Features represented in the application |
| --- | --- |
| Authentication | Registration, sign-in, password recovery/verification UI, logout, role-aware navigation |
| Learner | Course search and browsing, course details, favorites, cart, enrolled courses, learning-progress/video UI, reviews |
| Instructor | Course CRUD, lesson management and materials, course reviews, instructor profile, revenue dashboard, withdrawal requests |
| Admin | User and instructor management, course review/approval, reviews moderation, statistics, analytics, platform settings |
| Commerce | Checkout interface, payment methods/history, payment and payout management interfaces |
| Localization | English and Arabic content, language detection/switching, RTL presentation |

**Important:** Some capabilities depend on a configured backend and third-party integrations. An interface or an API client in this repository does not, by itself, guarantee a currently operational payment transaction, social sign-in, email delivery, or hosted workflow.

## Technology stack

### Front end

| Category | Technology |
| --- | --- |
| UI | React 19, TypeScript |
| Build | Vite 7 |
| Styling | Tailwind CSS, Radix UI, responsive layouts |
| Routing | React Router |
| Server state | TanStack Query |
| HTTP | Axios with a shared instance/interceptors |
| Forms | Formik, Yup (plus React Hook Form dependency) |
| Data visualization | Recharts |
| Localization | i18next, react-i18next |
| Notifications | Sonner |
| Checkout UI | Stripe client packages and Laravel-facing payment APIs |
| Tooling | ESLint, TypeScript checks |

### Associated backend (separate repository)

- PHP 8.2+ / Laravel 12
- MySQL
- Laravel Sanctum for authenticated API routes
- Laravel controllers and REST endpoints for users, courses, lessons, reports, revenue, and payments
- Integrations/configuration for external services such as Stripe and social authentication

The backend is **not** included in this front-end repository.

## Front-end project organization

```text
src/
├── api/           # HTTP service functions for individual domains
├── components/    # Shared UI, learner, instructor and admin components
├── data/          # Local UI/sample data used in some views
├── hooks/         # Reusable hooks and TanStack Query hooks
├── i18n/          # Internationalization initialization
├── lib/           # Axios instance, query keys, shared helpers/types
├── pages/         # Page-level interfaces
├── routes/        # App routes and client-side route guards
├── schemas/       # Form/data validation schemas
├── types/         # Domain types
└── utils/         # Utilities
```

## Run the front end locally

### Prerequisites

- **Node.js 20.19+ or 22.12+** (Vite 7 requirement)
- npm
- Access to a running instance of the Laravel API for API-driven features

```bash
git clone https://github.com/MohammedNasr51/round-5-front-ByWay.git
cd round-5-front-ByWay
npm ci
```

Create a local `.env` in the front-end repository:

```dotenv
# Trailing slash is intentional; API service paths are relative to this base URL.
VITE_API_URL=http://127.0.0.1:8000/api/

# Only needed when using an appropriately configured Stripe client flow.
# Publishable keys are public; never put a Stripe secret key in a Vite variable.
VITE_STRIPE_PUBLISHABLE_KEY=your_test_publishable_key
```

Then run:

```bash
npm run dev
```

Additional scripts:

```bash
npm run build       # TypeScript build + Vite production bundle
npm run type-check  # TypeScript checking
npm run lint        # ESLint
npm run preview     # Preview a previously built bundle
```

> If the Laravel API is unavailable, you may still view parts of the interface, but authenticated and data-driven workflows will fail. There is **no automatically enabled mock-server mode** in the current repository.

## Run the Laravel API locally (separate team repository)

> These are baseline Laravel setup instructions, **not a claim that all third-party workflows run without additional configuration**. Adjust for your local database, queue, mail, storage, CORS, and provider settings. Check the backend's own README and configuration for project-specific requirements.

Prerequisites: **PHP 8.2+**, Composer, MySQL, and required PHP extensions.

```bash
git clone https://github.com/Huma-volve/round5-byway.git byway-api
cd byway-api
composer install
cp .env.example .env
php artisan key:generate
```

On Windows Command Prompt, use `copy .env.example .env` instead of `cp`.

Edit the backend `.env` with valid local database settings, for example:

```dotenv
APP_ENV=local
APP_DEBUG=true
APP_URL=http://127.0.0.1:8000
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=byway
DB_USERNAME=your_local_user
DB_PASSWORD=your_local_password
```

Create the corresponding MySQL database, then run:

```bash
php artisan migrate
php artisan serve --host=127.0.0.1 --port=8000
```

If the specific workflows you test require file uploads, asynchronous jobs, demo data, mail, OAuth, or payment processing, additional setup may be necessary (for example `php artisan storage:link`, a configured queue worker, seeders if available, and provider test credentials). Configure CORS to allow the front-end development origin.

**Never commit `.env` files, production API keys, real payment credentials, or real user data.**

## How the front end communicates with the backend

```text
React pages/components
        |
        v
Custom hooks / TanStack Query
        |
        v
Domain API modules (src/api)
        |
        v
Shared Axios instance + auth token
        |
        v
Laravel REST API / Sanctum middleware
        |
        v
MySQL and backend integrations
```

Client-side route guards improve navigation and user experience; **authorization must still be enforced by Laravel on the server**.

## Collaboration and attribution

ByWay was developed as a **team internship project** at **Huma-volve**. The front-end README originally identified four participating trainees: **Mohamed, Ola, Mennah, and Asmaa**, with features shared across authentication, learner, instructor, and admin workstreams. My own contributions are identified above and linked to the original organization's Git history.

This fork is presented to document my participation and engineering work. The full product, all designs, and the Laravel backend should not be attributed exclusively to me.

## Current limitations and future improvements

- Original production Laravel backend is not currently hosted, so the public front end is not an end-to-end functioning demo.
- Third-party payments, email notifications, storage, and OAuth require valid development/test configurations; do not use live transactions for portfolio testing.
- A dedicated browser-based demo mode, reproducible seed data, and expanded automated tests would make the project easier to evaluate.
- Future portfolio improvements: deployment, verified end-to-end sample journeys, screenshots, an architecture diagram, and better onboarding documentation.

## Ownership and licensing

This is a collaborative internship codebase. The public front-end repository does not currently declare a license; do not assume it is freely relicensable or that every contributor's work is mine. Refer to Huma-volve and the original contributors for ownership and reuse terms.
