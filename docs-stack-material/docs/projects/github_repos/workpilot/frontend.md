# Frontend Architecture

The WorkPilot client is a modern web application built with **Next.js (App Router)** and **TypeScript**. It is designed to be highly responsive, typesafe, and easy to maintain.

---

## 1. Directory Organization

The Next.js frontend utilizes the App Router paradigm, strictly separating UI components from API integration logic.

```text
frontend/
├── app/                  # Next.js App Router (Pages, Layouts, Routing)
│   ├── (auth)/           # Route group for Login/Register (No Dashboard Layout)
│   ├── tenant/           # Tenant Dashboard Routes
│   ├── layout.tsx        # Global Layout
│   └── page.tsx          # Landing Page
├── components/           # Reusable React UI Components
│   ├── ui/               # Base design system components (Buttons, Inputs)
│   └── auth/             # Domain-specific components (LoginForm)
├── lib/                  # Utilities, Axios instances, Types
└── use-cases/            # API Integration Layer (React Query / Axios calls)
```

---

## 2. API Integration Layer (`use-cases`)

Instead of making `axios.get()` calls directly inside React components, all API calls are abstracted into the `use-cases` directory.

### Why?
1. **Reusability:** The `loginUser` function can be used in the LoginForm component, or in an end-to-end testing script.
2. **Separation of Concerns:** Components shouldn't care *how* data is fetched, only how to render it.

### Axios Interceptors & Credentials
The core Axios instance is configured with `withCredentials: true`. This is vital. It tells the browser to automatically attach the `HttpOnly` refresh token cookie to outgoing requests made to the FastAPI backend.

Furthermore, an Axios Interceptor is configured to intercept `401 Unauthorized` responses. If a request fails due to an expired access token, the interceptor automatically calls the `/auth/refresh` endpoint (which uses the HttpOnly cookie), gets a new access token, and transparently retries the original failed request.

---

## 3. State Management & Validation

- **Form Validation:** WorkPilot uses **Zod** paired with **React Hook Form**. This provides robust, end-to-end type safety. The Zod schemas on the frontend often mirror the Pydantic schemas on the backend, ensuring data integrity before the request even leaves the browser.
- **Global State:** (Future Design) For complex state sharing across distant components (like user profile data or theme preferences), lightweight state managers like Zustand or React Context are utilized over heavier solutions like Redux.

---

## 4. The UI / UX Layer

- **TailwindCSS:** Utility-first styling is used exclusively. It prevents CSS bundle bloat and keeps styling collocated with the component logic.
- **Shadcn UI (or similar):** Base components are built to be accessible (ARIA compliant) and highly customizable.
