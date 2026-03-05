# Fullstack Blog — System Design Sandbox

## 1. Project Philosophy

**"Not just a blog, but an engineering experiment."**

This project is a full-stack application deployed on AWS, designed specifically to serve as a **system-design sandbox**. The goal was not content creation, but to stress-test real production concerns that are often skipped in tutorial projects.

It forces the developer to reason about critical trade-offs: **token lifecycle management, cache boundaries, failure modes, deployment friction, and observability gaps.**

## 2. Core Engineering Pillars

### 2.1 Operational Correctness
Beyond standard features, the system implements rigorous operational standards:

*   **Request Tracing**: Request-scoped IDs and structured logging for complete traceability across services.
*   **Standardized Responses**: API envelopes (`{ data, meta, error }`) to decouple clients from backend changes.
*   **Resiliency Patterns**:
    *   **Soft Deletes**: Non-destructive operations to preserve data integrity.
    *   **Health Checks**: Dedicated endpoints for infrastructure visibility.
    *   **Environment Validation**: "Fail fast" mechanisms to prevent silent configuration failures.
*   **Frontend Robustness**: Centralized error mapping, automatic retries, and timeout handling.

### 2.2 Security & Identity
*   **Advanced JWT Auth**: Access/refresh token separation with **token versioning** and **forced invalidation** on password changes.
*   **Edge Protection**: Rate-limiting implemented at the authentication edge to control abuse.
*   **Feature Flags**: Capability to ship code safely without redeploying.

### 2.3 DevOps & Infrastructure
*   **Environment Parity**: Fully dockerized frontend and backend to ensure "works on my machine" means "works in production".
*   **CI/CD Pipelines**: GitHub Actions acting as a strict quality gate for automated testing and deployment.
*   **Configuration Discipline**: Strict separation of local vs. cloud configuration.

## 3. Architecture Overview

### Containerized Microservices
The application is composed of isolated services running in Docker containers, orchestrated for AWS deployment.

`Client (Vite/React) ↔ Nginx (Reverse Proxy) ↔ Django application ↔ PostgreSQL`
                                          `↕`
                                        `Redis`

### Technology Stack
*   **Backend**: Django 4.2 + DRF (API Versioning Ready)
*   **Frontend**: React 18 + Vite
*   **Database**: PostgreSQL 15
*   **Caching**: Redis (Token Blacklist)
*   **Infrastructure**: AWS (EC2/RDS), Docker Compose

## 4. API Specification

| Method | Endpoint | Description | Design Pattern |
| :--- | :--- | :--- | :--- |
| `POST` | `/api/v1/auth/token/` | Obtain Pair | **Rate Limited** |
| `POST` | `/api/v1/auth/refresh/` | Rotate Token | **Token Versioning** |
| `POST` | `/api/v1/auth/logout/` | Revoke Token | **Blacklisting** |
| `GET` | `/api/v1/posts/` | List Posts | **Standard Envelope** |

## 5. Future Roadmap

Next iterations are focused on deepening the engineering complexity:
*   **Caching Strategy**: Implementing sophisticated cache invalidation patterns.
*   **Background Jobs**: Asynchronous processing for non-blocking operations.
*   **Observability**: Enhanced metrics and tracing.

## 6. Installation & Deployment

### Docker (Recommended)

```bash
git clone https://github.com/ashif-ek/fullstack-blog-jwt-docker.git
cd fullstack-blog-jwt-docker
docker-compose up --build -d
```

### Manual Setup (Dev)

1.  **Backend**:
    ```bash
    pip install -r requirements.txt
    python manage.py migrate
    python manage.py runserver
    ```
2.  **Frontend**:
    ```bash
    npm install
    npm run dev
    ```

## 7. Summary
This project is a testament to the belief that **engineering maturity** comes from handling edges cases, failure modes, and deployment realities, not just shipping features.
