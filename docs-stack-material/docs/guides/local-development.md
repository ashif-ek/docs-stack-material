# Local Development Guide

This guide covers the general workflow for working with the projects locally.

## Prerequisite Tools
Ensure you have the following installed:
*   Git
*   Node.js (LTS version)
*   Python (3.10+)
*   VS Code (Recommended IDE)

## Setting Up a Project
1.  **Clone**: `git clone <url>`
2.  **Env Vars**: Create `.env` from `.env.example`.
3.  **Dependencies**: `npm install` or `pip install -r requirements.txt`.

## Running Servers
*   **Frontend**: Usually runs on `http://localhost:5173` (Vite) or `3000` (Next.js).
*   **Backend**: Usually runs on `http://localhost:8000` (Django/FastAPI) or `5000` (Node/Express).

## Debugging
*   **Frontend**: Use React Developer Tools.
*   **Backend**: Check terminal logs for stack traces. Use `pdb` for Python debugging if needed.