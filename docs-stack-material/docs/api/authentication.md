# Authentication API

Secure access handling across applications.

## JWT Implementation

Projects like **Fullstack Blog** and **Student Management** use JSON Web Tokens (JWT).

### Flow
1.  **Login**: `POST /api/token/`
    *   Payload: `{username, password}`
    *   Response: `{access, refresh}`
2.  **Access Protected Routes**:
    *   Header: `Authorization: Bearer <access_token>`
3.  **Refresh Token**: `POST /api/token/refresh/`
    *   Payload: `{refresh}`

## Admin Access

Admin panels are protected via session auth or specific internal roles.
*   **Django Admin**: `/admin/` (Standard Django auth).
*   **Portfolio Admin**: Custom implementation.