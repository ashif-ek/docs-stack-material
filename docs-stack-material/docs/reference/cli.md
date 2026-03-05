# Command Line Interface (CLI) Reference

This document serves as a comprehensive reference for the essential command-line operations utilized across the various stacks within this project ecosystem. Mastery of these commands is crucial for efficient development, testing, and deployment workflows.

---

## 🟢 Node.js & npm Ecosystem

These commands are foundational for frontend projects utilizing React, Vite, and related Javascript tooling.

| Command | Description | Use Case |
| :--- | :--- | :--- |
| `npm install` | Resolves and installs all dependencies listed in `package.json`. | Run immediately after cloning a repository or pulling new dependency updates. |
| `npm run dev` | Initializes the local development server with Hot Module Replacement (HMR) enabled. | Use during active UI development for instant feedback. |
| `npm run build` | Compiles the application into highly optimized, static assets ready for deployment. | Execute prior to deploying to a production environment (e.g., Vercel, Netlify). |
| `npm run lint` | Triggers static code analysis via ESLint to ensure code quality and style consistency. | Run before committing changes to adhere to project standards. |
| `npm test` | Executes the test suite (if configured, e.g., via Vitest or Jest) to validate application logic. | Run continuously during development to prevent regressions. |

---

## 🐍 Python & Django Environment

The following commands are specific to the Django framework, managing everything from the local server to database schema migrations.

| Command | Description | Use Case |
| :--- | :--- | :--- |
| `python manage.py runserver` | Starts the lightweight Django development server. | Use for local backend API development and testing. |
| `python manage.py makemigrations` | Scans models for changes and generates new migration scripts. | Run whenever you alter `models.py` definitions. |
| `python manage.py migrate` | Applies pending migration scripts to synchronize the database schema. | Run after `makemigrations` or when pulling changes that include new migrations. |
| `python manage.py createsuperuser` | Prompts for credentials to create a new administrative user. | Use when initializing a fresh database to access the `/admin/` dashboard. |
| `python manage.py test` | Discovers and executes all registered unit and integration tests. | Essential for continuous integration and maintaining backend stability. |

---

## ⚡ Python & FastAPI Ecosystem

For high-performance API development leveraging FastAPI and Uvicorn.

| Command | Description | Use Case |
| :--- | :--- | :--- |
| `uvicorn main:app --reload` | Launches the ASGI server utilizing the `main.py` entry point (`app` instance) with auto-reloading enabled. | The primary command for active local development. |
| `pip install -r requirements.txt` | Installs Python packages specified in the requirements file. | Run when setting up the environment or when dependencies are updated. |

---

## 🐳 Docker Operations (Containerization)

For projects leveraging Docker for isolated development and deployment phases.

| Command | Description | Use Case |
| :--- | :--- | :--- |
| `docker-compose up --build` | Builds container images and starts the entire multi-container application. | Use to spin up complex environments (e.g., App + DB + Redis) simultaneously. |
| `docker-compose down` | Stops and safely removes containers, networks, and optionally volumes. | Run to cleanly shut down the local containerized environment. |

> **Pro Tip:** Always utilize a virtual environment (`venv` or `conda`) when working with Python projects, and ensure you run `npm install` before attempting to start any JavaScript development server.