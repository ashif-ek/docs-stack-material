# Conventions

To maintain consistency across projects, the following conventions are generally observed.

## Code Style
*   **Formatting**: Prettier for JavaScript/React; Black for Python.
*   **Linting**: ESLint for JS; Flake8/Pylint for Python.

## Commit Messages
We follow the **Conventional Commits** specification:

*   `feat: ...` for new features.
*   `fix: ...` for bug fixes.
*   `docs: ...` for documentation updates.
*   `style: ...` for formatting changes.
*   `refactor: ...` for code refactoring.

## Branching
*   `main` / `master`: Production-ready code.
*   `dev`: Development branch (if applicable).
*   `feature/<name>`: New feature development.
*   `bugfix/<name>`: Bug fixes.

## File Naming
*   **React Components**: PascalCase (e.g., `Button.tsx`, `Navbar.jsx`).
*   **JS/TS Utilities**: camelCase (e.g., `formatDate.ts`).
*   **Python Modules**: snake_case (e.g., `utils.py`, `models.py`).