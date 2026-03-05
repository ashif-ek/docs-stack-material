# Development Conventions & Standards

To ensure long-term maintainability, seamless developer onboarding, and a cohesive codebase across all distributed projects, we strictly enforce the following development conventions. 

---

## 🎨 Code Style & Quality Assurance

Automated tooling is leveraged to eliminate subjective style debates and mathematically ensure code quality.

*   **JavaScript/TypeScript Ecosystem**:
    *   **Formatting**: **Prettier** is the absolute authority on code formatting. It is enforced via pre-commit hooks.
    *   **Linting**: **ESLint** is utilized to catch logical errors, enforce React hooks rules, and maintain architectural boundaries.
*   **Python Ecosystem**:
    *   **Formatting**: **Black** ("The Uncompromising Code Formatter") is used to strictly dictate Python syntax and structure.
    *   **Linting**: **Flake8** or **Pylint** are deployed to analyze code complexity, enforce PEP 8 standards, and detect code smells.

---

## 📝 Version Control & Commit Protocol

We mandate the **Conventional Commits** specification (v1.0.0) to maintain a readable, automatically parseable project history. This allows for automated semantic versioning and changelog generation.

**Format**: `<type>[optional scope]: <description>`

*   `feat: ...` : Introduces a new feature to the codebase (correlates with MINOR semantic versioning).
*   `fix: ...` : Patches a bug in the existing codebase (correlates with PATCH semantic versioning).
*   `docs: ...` : Modifications exclusively to documentation (e.g., README, MkDocs).
*   `style: ...` : Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc).
*   `refactor: ...` : A code change that neither fixes a bug nor adds a feature, but improves internal structure.
*   `test: ...` : Adding missing tests or correcting existing test suites.

---

## 🌿 Branching Strategy

The repository structure follows a simplified Git Flow model tailored for continuous delivery.

*   `main` (or `master`): The single source of truth. Represents the stable, production-deployed state of the application. Commits here automatically trigger production deployments.
*   `dev` (or `develop`): The active integration branch for ongoing development.
*   `feature/<ticket-or-name>`: Ephemeral branches extending from `dev` utilized exclusively for building new features (e.g., `feature/user-auth-flow`).
*   `bugfix/<ticket-or-name>`: Branches dedicated to resolving specific anomalies (e.g., `bugfix/payment-gateway-timeout`).

---

## 🗂️ File Naming Nomenclature

Uniform file naming ensures predictable navigation across massive project structures.

*   **React/Frontend Components**: Always utilize **PascalCase**.
    *   *Example*: `UserProfileHeader.tsx`, `PrimaryButton.jsx`.
*   **TypeScript/JavaScript Utilities**: Always utilize **camelCase** for non-component logic files.
    *   *Example*: `formatDate.ts`, `apiClient.ts`.
*   **Python Modules & Packages**: Strictly adhere to **snake_case**, per PEP 8 standards.
    *   *Example*: `database_utils.py`, `user_models.py`.