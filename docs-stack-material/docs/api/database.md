# Data Modeling & Persistence

This section outlines the architectural approach to data structure, storage mechanisms, and Object-Relational Mapping (ORM) interaction paradigms utilized across the backend systems within this portfolio.

---

## 🗃️ Core Domain Models

While schemas vary drastically depending on business requirements, we adhere to strict normalization standards and utilize universally identifiable base models across all RDBMS applications.

### The Universal User Model
Almost all applications extend a foundational `User` abstraction incorporating stringent validation:
*   `id`: Primary Key (Universally Unique Identifier - UUIDv4 strongly preferred over standard Auto-Incrementing Integers for security).
*   `username`: Indexed String, enforces global uniqueness.
*   `email`: Indexed String, enforces global uniqueness with regex validation.
*   `is_active` / `is_staff`: Boolean flags dictating system access levels.

### Domain-Specific Architectures
*   **E-Commerce Systems**: Architected around relational stability. Core entities include `Product` (catalog item), `Order` (transaction record), `CartItem` (ephemeral session relation), and `PaymentTransaction`.
*   **Educational Platforms**: Designed for complex matrix relationships. Entities include `Student` (User subset), `Course` (curriculum data), and `Enrollment` (Many-to-Many resolution table).
*   **Analytics Engines (Salary)**: Optimized for rapid querying and aggregation. Features isolated tables like `SalaryData` mapping `job_role`, `experience_years`, `city`, and `compensation_amount`.

---

## 🔌 ORM Integration Paradigms

Direct SQL string manipulation is strictly forbidden to prevent SQL Injection vulnerabilities. We interact with the persistence layer exclusively through robust Object-Relational Mappers (ORMs).

*   **Django ORM Engine**: Utilized for Python monoliths. Heavily leverages QuerySets for lazy-loading and optimized SQL translation.
    *   *Syntax Pattern*: `TargetModel.objects.filter(is_active=True).select_related('profile')`
*   **SQLAlchemy Engine**: Utilized for FastAPI microservices. Provides a powerful, session-based declarative mapping paradigm.
    *   *Syntax Pattern*: `session.query(TargetModel).filter(TargetModel.is_active == True).all()`
*   **Mongoose (NoSQL)**: Utilized when interacting with MongoDB, allowing for schema validation at the application layer before pushing direct BSON object manipulations to the database.