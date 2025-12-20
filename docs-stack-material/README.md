# Docs Stack Material

Professional documentation system built with **MkDocs** and **Material for MkDocs**.

## 🚀 How to Run Locally

1.  **Activate the environment** (if not already active):
    ```powershell
    # From the project root (d:\ashif-dev)
    .\env\Scripts\Activate.ps1
    ```
2.  **Navigate to the docs folder**:
    ```powershell
    cd docs-stack-material
    ```
3.  **Start the development server**:
    ```bash
    mkdocs serve
    ```
    Your site will be available at [http://127.0.0.1:8000](http://127.0.0.1:8000).

## ☁️ How to Deploy (GitHub Pages)

1.  **Initialize Git** (one-time setup):
    ```bash
    git init
    git add .
    git commit -m "Initial commit"
    ```
2.  **Add your GitHub Repository**:
    ```bash
    # Replace with your actual repo URL
    git remote add origin https://github.com/<username>/<repo-name>.git
    ```
3.  **Deploy**:
    ```bash
    mkdocs gh-deploy
    ```
    This command builds your static site and pushes it to the `gh-pages` branch.