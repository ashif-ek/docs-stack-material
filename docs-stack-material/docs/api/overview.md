# API Documentation

This section provides an overview of the APIs exposed by the various backend services.

## Available APIs

### Implementation Details
Most backends in this portfolio are self-documenting:
*   **FastAPI & Django (DRF)**: Automatically generate Swagger/OpenAPI documentation.
*   Visit `/docs` or `/redoc` on the running backend server to explore endpoints interactively.

### Key Service Endpoints

#### Salary Checker
*   `GET /salary/insights`: Retrieve percentile data.
*   `POST /salary/predict`: ML-based salary prediction.

#### Portfolio Backend
*   `GET /projects`: List all projects.
*   `POST /messages`: Submit contact form data.

#### Noirel Ecommerce
*   `GET /products`: Fetch catalog.
*   `POST /cart`: Manage shopping cart.
*   `POST /orders`: Place a new order.

Refer to the individual project repositories for the most up-to-date API contracts.