# Architecture Decision Records (ADR)

This section documents the engineering rationale behind the core technologies and architectural patterns chosen for WorkPilot. Understanding these decisions is crucial for onboarding and future technical discussions.

---

## Why Microservices (or Service-Oriented Architecture)?

**Context:** The application needs to scale horizontally. Different domains (Auth, Billing, Core App) have different scaling profiles and security requirements.
**Decision:** We adopted a modular, service-oriented architecture (starting with a monolithic repository structured as logical microservices, e.g., `auth-service`).
**Trade-offs:** Increases deployment complexity but provides clean domain boundaries and allows teams to deploy independently in the future.

## Why FastAPI?

**Context:** We needed a high-performance backend framework capable of handling asynchronous I/O (essential for multi-tenant database routing).
**Decision:** Selected FastAPI (Python).
**Alternatives:** Django, Express (Node.js), Go.
**Trade-offs:** 
- *Pros:* Exceptional performance (ASGI), native Pydantic validation, automatic OpenAPI generation, type-hinting support.
- *Cons:* Smaller ecosystem compared to Django; requires strict architectural discipline to prevent code turning into a "big ball of mud."

## Why Next.js (App Router)?

**Context:** The frontend requires robust SEO for marketing pages, but a highly interactive, SPA-like feel for the dashboard.
**Decision:** Next.js 14+ utilizing the App Router.
**Alternatives:** React (Vite/CRA), Vue/Nuxt, SvelteKit.
**Trade-offs:**
- *Pros:* Server Components (RSC) reduce client bundle size; fantastic routing; strong ecosystem.
- *Cons:* Steeper learning curve for RSC vs. traditional React; complex caching mechanisms.

## Why SQLAlchemy & Alembic?

**Context:** We need a reliable ORM that supports advanced PostgreSQL features, specifically dynamic schema switching for multi-tenancy.
**Decision:** SQLAlchemy 2.0 with Alembic for migrations.
**Trade-offs:** SQLAlchemy is heavy and has a steep learning curve, but it provides unparalleled control over transactions and schema execution contexts.

## Why Schema-per-Tenant?

**Context:** B2B SaaS customers demand absolute data isolation.
**Decision:** PostgreSQL Schema-per-Tenant.
**Alternatives:** 
- *Database-per-tenant:* Too expensive and complex to orchestrate.
- *Shared-table (tenant_id column):* Too risky; one missing `WHERE` clause causes data leaks.
**Consequences:** Migrations (Alembic) must be run iteratively across all schemas. Connection pooling needs careful management to prevent cross-schema contamination on reused connections.

## Why HTTPOnly Cookies (Over localStorage)?

**Context:** Storing JWT access/refresh tokens in `localStorage` exposes them to Cross-Site Scripting (XSS) attacks. If an attacker injects a malicious script, they can steal tokens and hijack accounts.
**Decision:** Refresh tokens are stored in `HttpOnly`, `Secure`, `SameSite=None` cookies.
**Trade-offs:** Requires strict CORS configuration and makes cross-domain API calls slightly more complex, but drastically improves security posture.

## Why uv (Package Manager)?

**Context:** Python's standard `pip` or `poetry` can be slow, especially in Docker build steps.
**Decision:** Adopted `uv` by Astral.
**Trade-offs:** It's an incredibly fast, Rust-based package installer. The only downside is it's relatively new, but it significantly accelerates CI/CD and local build times.
