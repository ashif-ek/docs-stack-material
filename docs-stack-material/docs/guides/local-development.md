# Local Development Environment Guide

Establishing a reliable and standardized local development environment is critical for seamless contribution to the projects within this portfolio. This guide dictates the required toolchains and standard operating procedures for local execution and debugging.

---

## 🛠️ Mandatory Prerequisites

Before cloning any project, ensure your host machine is equipped with the following underlying technologies:

*   **Version Control**: Git (Latest stable release)
*   **Javascript Ecosystem**: Node.js (v18+ Active LTS recommended) & npm/yarn
*   **Python Ecosystem**: Python (v3.10+) & pip
*   **Virtualization** *(Optional but recommended)*: Docker & Docker Compose for complex, multi-service architectures like the Fullstack Blog.
*   **IDE**: Visual Studio Code (VS Code) is highly recommended due to its extensive extension ecosystem (Prettier, ESLint, Python, Docker).

---

## 🔄 Standard Initialization Protocol

Regardless of the project's underlying language, the bootstrapping process conceptually follows these three phases:

1.  **Source Retrieval**:
    ```bash
    git clone https://github.com/ashif-ek/<target-repository>.git
    cd <target-repository>
    ```
2.  **Environment Variable Hydration**:
    Every isolated project contains an `.env.example` baseline. Duplicate this file, rename it to `.env`, and populate the explicit values required for your local setup (e.g., local database URIs).
3.  **Dependency Instantiation**:
    *   *Node.js*: Run `npm install`
    *   *Python*: Run `python -m venv venv` followed by activating the environment and `pip install -r requirements.txt`.

---

## 🚀 Execution & Port Conventions

To prevent port conflicts when running multiple services simultaneously (e.g., a React frontend and a Django backend), projects default to the following port allocations:

### Frontend Clients
*   **Vite Interfaces (React)**: Bound to `http://localhost:5173`
*   **Next.js SSR Applications**: Bound to `http://localhost:3000`

### Backend APIs
*   **Django / FastAPI Services**: Bound to `http://localhost:8000`
*   **Node.js / Express Services**: Expose endpoints on `http://localhost:5000`

---

## 🐞 Debugging Strategies

*   **Frontend**: Heavily leverage the *React Developer Tools* browser extension to inspect component hierarchies and verify Redux/Zustand state mutations in real-time.
*   **Backend (Python)**: Utilize standard system-out logs for immediate stack traces. For complex logical deadlocks, inject `import pdb; pdb.set_trace()` (or the built-in `breakpoint()` function in Python 3.7+) to halt execution and inspect local memory states.