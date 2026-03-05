# Operational Installation Protocols

This document outlines the standardized operational procedures for cloning, bootstrapping, and executing projects from the repository network. While individual application architectures (e.g., Python monoliths vs. React Single Page Applications) necessitate specific commands, the foundational setup sequence remains consistent across the entire portfolio.

---

## 🔄 The Universal Bootstrap Sequence

Adhere to these foundational steps when initializing any project locally.

### 1. Source Code Acquisition
Initiate the setup by securely pulling the latest stable source code from the primary VCS repository.
```bash
git clone https://github.com/ashif-ek/<target-repository-name>.git
cd <target-repository-name>
```

### 2. Dependency Resolution

Proper isolation of project dependencies is critical for system stability. Select the path appropriate for the application's core runtime environment:

**A. Node.js Ecosystem (Javascript/TypeScript/React)**
Our preferred node package manager handles full resolution of the dependency tree defined in `package.json`.
```bash
npm install
# Alternatively, if explicitly required by the repository's lockfile:
yarn install
```

**B. Python Ecosystem (Django/FastAPI)**
It is **mandatory** to establish an isolated virtual environment before modifying any system-level Python packages.
```bash
# Generate the virtual environment named 'venv'
python -m venv venv

# Activate the isolated environment
# macOS/Linux:
source venv/bin/activate  
# Windows (PowerShell/CMD):
venv\Scripts\activate

# Install the strict dependency requirements
pip install -r requirements.txt
```

### 3. Environment Configuration Injection
Almost all applications require secure, local environmental variables to function correctly (e.g., API keys, Database URLs).
*   Locate the specific environment documentation or review the `.env.example` file located at the project root.
*   Duplicate this file, rename it exactly to `.env`, and populate it with your local development credentials. *See [Configuration Standards](configuration.md) for detailed policies on secrets management.*

### 4. Application Initialization
Launch the local development server tailored to the specific framework in testing.

*   **Vite / React / Node Ecosystem**: Initiates the dev server with HMR.
    ```bash
    npm run dev
    ```
*   **Python (Django Monolith)**: Starts the synchronous WSGI development server.
    ```bash
    python manage.py runserver
    ```
*   **Python (FastAPI Microservices)**: Boots the high-performance ASGI server with directory watching enabled.
    ```bash
    uvicorn main:app --reload
    ```

---

## 📘 Project-Specific Documentation Paths

For deeply complex setups involving database migrations, custom scripts, or Docker orchestration, always refer strictly to the exact project's dedicated protocol page:

*   **[Portfolio React Setup Protocol](projects/github_repos/portfolio-react.md#installation)**
*   **[Noirel Enterprise Installation](projects/github_repos/noirel-ecommerce.md#installation-setup)**
*   **[Salary Analytics Configuration](projects/github_repos/salary-checker.md#setup-instructions)**
*   **[Time Lens Deployment Steps](projects/github_repos/time-lens-python.md#run-locally)**