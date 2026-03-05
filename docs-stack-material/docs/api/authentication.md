# Authentication & Authorization

Securing endpoints and managing identity is paramount. Across this portfolio, authentication mechanisms are explicitly chosen based on the architectural needs of the specific project, ranging from stateless token-based authentication for decoupled SPAs to secure session-handlers for monolithic admin panels.

---

## 🔑 JSON Web Token (JWT) Implementation

For heavily decoupled applications like the **Fullstack Blog** and the **Student Management System**, we uniformly implement the **JWT (JSON Web Token)** standard. This ensures scalable, stateless authentication across diverse frontends.

### The Token Lifecycle Flow

1.  **Credential Verification (Login)**
    *   **Endpoint**: `POST /api/token/`
    *   **Payload Requirement**: `{ "username": "...", "password": "..." }`
    *   **Successful Response**: The API responds with two cryptographically signed tokens: `{ "access": "<short-lived-token>", "refresh": "<long-lived-token>" }`.
2.  **Accessing Protected Resources**
    *   To access any protected endpoint, the client must inject the `access` token into the request payload's Authorization header.
    *   **Header Format**: `Authorization: Bearer <access_token>`
3.  **Session Continuation (Token Refresh)**
    *   **Endpoint**: `POST /api/token/refresh/`
    *   **Payload Requirement**: `{ "refresh": "<refresh_token>" }`
    *   Once the `access` token expires naturally, the client silently utilizes the `refresh` token to acquire a fresh `access` token without requiring the user to re-authenticate manually.

---

## 🛡️ Administrative Access Management

Administrative dashboards and high-privilege operations require rigorous, often stateful, security paradigms.

*   **Django Admin Workspaces**: Applications leveraging Django (e.g., Student Management) utilize its battle-tested, built-in session authentication mechanism globally restricted to the `/admin/` routes. This is strictly guarded by CSRF tokens and internal permission classes.
*   **Custom Portfolio Dashboards**: Projects with bespoke admin interfaces utilize customized Role-Based Access Control (RBAC) layers baked directly into the JWT payload or verified via specialized middleware prior to route execution.