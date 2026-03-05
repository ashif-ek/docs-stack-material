# Configuration & Environment Variables

Proper configuration management is critical for operational security and application behavior across different environments (Development, Staging, Production). This document outlines the core environment variables utilized across the overarching tech stack.

---

## 🔐 Core System Variables

These variables dictate fundamental application behaviors and security postures.

| Variable | Description | Requirement Level | Default Value | Security Note |
| :--- | :--- | :--- | :--- | :--- |
| `DEBUG` | Toggles detailed error tracebacks and development-specific behaviors. | **Optional** | `False` | **CRITICAL:** *Must* explicitly be set to `False` in production to prevent source code leaks. |
| `SECRET_KEY` | Cryptographic key utilized for signing session cookies, JWTs, and password hashing salts. | **Mandatory** | *None* | Must be a long, cryptographically secure random string. Never commit to version control. |
| `ALLOWED_HOSTS` | Comma-separated list of host/domain names the application is permitted to serve securely. | **Mandatory** | `*` (Dev only) | Required in production to mitigate HTTP Host header attacks. |

---

## 🗄️ Database & Infrastructure

Determines how the application connects to stateful persistence layers.

| Variable | Description | Requirement Level | Typical Format |
| :--- | :--- | :--- | :--- |
| `DATABASE_URL` | The fully qualified connection string detailing the RDBMS dialect, credentials, host, and database name. | **Mandatory** | `postgres://user:pass@host:5432/dbname` |
| `REDIS_URL` | Connection string for the Redis instance used for caching or Celery task brokering. | **Optional** | `redis://localhost:6379/1` |
| `PORT` | The port on which the web server process should bind and listen. | **Optional** | `8000` (Python), `3000`/`5173` (Node) |

---

## 🌐 Network & Access Control

These variables govern cross-origin resource sharing and external service communication.

| Variable | Description | Requirement Level | Use Case |
| :--- | :--- | :--- | :--- |
| `CORS_ORIGIN` | Defines the specific frontend origins allowed to send requests to the backend API. | **Mandatory** | e.g., `https://my-frontend-app.com`. Used to prevent unauthorized cross-origin data reads. |
| `API_BASE_URL` | The root URL utilized by frontend clients to communicate with the backend. | **Optional** | Set in frontend `.env` to easily switch between local backend and production endpoints. |

---

## 🔒 Security Best Practices

1. **Environment Separation**: Always maintain strictly segregated `.env` files for distinct environments (`.env.development`, `.env.production`).
2. **Never Commit Secrets**: Ensure `.env` is comprehensively included in your global `.gitignore`. Use `.env.example` to document required variables safely via template.
3. **Secret Rotation**: Regularly rotate high-value secrets like `SECRET_KEY` or third-party API keys, especially after a personnel change or suspected breach.

For practical application guidelines within specific frameworks, refer to the [General Configuration Guide](../configuration.md).