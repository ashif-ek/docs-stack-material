# API Architecture Overview

This section outlines the design philosophies and technical specifications of the Application Programming Interfaces (APIs) exposed by the various backend microservices and monoliths within this portfolio. Our APIs are designed fundamentally around **RESTful principles**, prioritizing predictability, statelessness, and robust error handling.

---

## 📖 Automated Documentation Strategies

To minimize integration friction and maintain a single source of truth, most backend services within this ecosystem are entirely **self-documenting**:

*   **FastAPI & Django REST Framework (DRF)**: Both frameworks natively generate and serve interactive OpenAPI (formerly Swagger) documentation schemas based directly on the application's route signatures and validation models.
*   **Interactive Exploration**: Developers can generally access the live, interactive API specification by navigating to `/docs` (Swagger UI) or `/redoc` (ReDoc) on any running local or production backend instance.

---

## 🌐 Core Service Endpoints Reference

Below is a high-level topographical map of critical endpoints across the flagship projects. *Note: Always refer to a project's live `/docs` route for the exact payload schemas and parameter requirements.*

### 🤖 Salary Reality Engine (FastAPI)
Focused on data analysis and ML inference.
*   `GET /salary/insights`: Retrieves comprehensive statistical percentile distributions given a role and location.
*   `POST /salary/predict`: Dispatches payload to the scikit-learn pipeline for ML-based salary forecasting.

### 💼 Portfolio Management Backend (Node/React CMS)
Handles dynamic content delivery for the developer portfolio.
*   `GET /api/projects`: Fetches the active catalog of portfolio projects.
*   `POST /api/messages`: Securely handles and persists incoming contact form submissions.

### 🛒 Noirel E-commerce API
A complex REST implementation handling critical transaction states.
*   `GET /api/products`: Retrieves the paginated, filter-ready product catalog.
*   `POST /api/cart`: Initializes or modifies the user's active shopping cart session.
*   `POST /api/orders`: Executes the checkout flow, integrating with payment gateways (Stripe/Razorpay) and locking inventory.

For exhaustive, parameter-level details, please consult the respective project repositories.