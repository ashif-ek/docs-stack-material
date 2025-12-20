# Database Schema & API

How data is structured and accessed.

## Models

### User Model (Common)
*   `id`: UUID or Integer.
*   `username`: String, unique.
*   `email`: String, unique.
*   `is_active`: Boolean.

### Domain Specific
*   **Ecommerce**: `Product`, `Order`, `CartItem`.
*   **Education**: `Student`, `Course`, `Enrollment`.
*   **Salary**: `SalaryData` (role, experience, city, amount).

## ORM Interaction

*   **Django ORM**: `Model.objects.filter(...)`
*   **SQLAlchemy**: `session.query(Model).filter(...)`
*   **Mongoose/JSON**: Direct object manipulation.