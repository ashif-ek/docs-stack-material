# Backend Architecture

The backend of WorkPilot is engineered using **FastAPI** (Python). It is structured using a Domain-Driven Design (DDD) approach, ensuring business logic is decoupled from HTTP transport layers.

---

## 1. Directory Structure

The `auth-service` (the core backend service) is organized as follows:

```text
auth-service/
├── src/
│   ├── core/              # Global configurations, environment variables, base exceptions
│   ├── infrastructure/    # DB connection pools, Middlewares (Tenant, RateLimit)
│   ├── modules/           # Domain logic (Auth, Users, Tenant, Employee)
│   │   ├── auth/
│   │   │   ├── router.py  # HTTP Endpoints (FastAPI)
│   │   │   ├── service.py # Business Logic
│   │   │   ├── schemas.py # Pydantic Validation Models
│   │   │   └── repository.py # Database Operations (SQLAlchemy)
│   └── main.py            # FastAPI Application Entrypoint
```

### Why this structure?
By separating `router.py` (Transport) from `service.py` (Business Logic) and `repository.py` (Data Access), the application becomes highly testable. You can unit test the `AuthService` without needing to spin up a FastAPI test client or an actual HTTP server.

---

## 2. The Dependency Injection Graph

FastAPI relies heavily on Dependency Injection (`Depends()`). This is used extensively to manage database sessions and authenticate users.

```python
@router.get("/me")
def get_current_user_info(
    current_user: dict = Depends(get_current_user_and_set_schema),
    db: Session = Depends(get_db)
):
    return {"user": current_user}
```

**`get_db`**: Yields a database session from the `request.state.db` (created by the `TenantMiddleware`), ensuring the endpoint uses the exact same transaction context.
**`get_current_user_and_set_schema`**: Extracts the Bearer token, validates the JWT signature, checks expiration, and returns the user payload.

---

## 3. Microservices & Domain Boundaries

Currently, WorkPilot operates as a "Modular Monolith". All domains (Auth, Users, Tenants) live within the `auth-service` codebase, but are strictly separated by folder (`src/modules/*`).

*(Future Design)*
As the engineering team grows, the codebase is designed so that `src/modules/billing` could be easily extracted into a completely separate `billing-service` running in a different Docker container, communicating via gRPC or message queues (RabbitMQ/Kafka).

---

## 4. Performance & Caching

- **Database Connection Pooling:** SQLAlchemy's `QueuePool` is used to manage connections efficiently across the uvicorn workers.
- **Async Processing:** While SQLAlchemy 2.0 supports async, the core logic currently utilizes thread-pools for blocking operations, handled seamlessly by FastAPI's `def` vs `async def` routing.
- **Future Caching:** Redis is planned for caching frequent read-heavy operations, such as Tenant resolution in the middleware.
