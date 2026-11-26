# Docs Stack – Material

Centralized engineering documentation portal and technical specifications repository for open-source applications, platforms, and architecture sandboxes by **Ashif E.K**.

Built with **MkDocs** and **Material for MkDocs**.

- **Live Documentation**: [https://ashif-ek.github.io/docs-stack-material/](https://ashif-ek.github.io/docs-stack-material/)
- **Author Portfolio**: [https://ashifek.in](https://ashifek.in)
- **GitHub Repository**: [https://github.com/ashif-ek/docs-stack-material](https://github.com/ashif-ek/docs-stack-material)

---

## Features

- **Standard Material Theme**: Clean, responsive layout with tab navigation and instant client-side search.
- **Theme Modes**: Seamless Light and Dark mode switching with system preference detection.
- **Architecture & API Reference**: Technical specifications, system architectures, data models, and deployment guides.
- **Project Catalog**: Comprehensive documentation for production systems and architectural lab prototypes.
- **Automated CI/CD**: Automatic deployment to GitHub Pages via GitHub Actions on every push to `main`.

---

## Project Structure

```text
.
├── .github/
│   └── workflows/
│       └── docs.yml             # GitHub Actions automated deployment workflow
├── docs-stack-material/
│   ├── mkdocs.yml               # MkDocs configuration file
│   ├── requirements.txt         # Documentation build dependencies
│   ├── docs/                    # Markdown content files
│   │   ├── index.md             # Portal homepage
│   │   ├── getting-started.md
│   │   ├── installation.md
│   │   ├── configuration.md
│   │   ├── architecture.md
│   │   ├── conventions.md
│   │   ├── api/                 # API specifications & auth guides
│   │   ├── guides/              # Dev, deploy, and customization guides
│   │   ├── projects/            # Project documentation & repo specs
│   │   └── reference/           # CLI & config references
│   └── site/                    # Generated static site output (git-ignored)
├── requirements.txt             # Root requirements
└── README.md
```

---

## Local Setup & Development

### 1. Prerequisites

- **Python 3.10+**
- **Git**

### 2. Clone Repository

```bash
git clone https://github.com/ashif-ek/docs-stack-material.git
cd docs-stack-material
```

### 3. Create & Activate Virtual Environment

**macOS / Linux:**
```bash
python3 -m venv env
source env/bin/activate
```

**Windows (PowerShell):**
```powershell
python -m venv env
.\env\Scripts\Activate.ps1
```

### 4. Install Dependencies

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

### 5. Start Local Development Server

Run from the repository root:

```bash
mkdocs serve -f docs-stack-material/mkdocs.yml
```

Or navigate to `docs-stack-material/` and run:

```bash
cd docs-stack-material
mkdocs serve
```

Open your browser and navigate to:
```text
http://127.0.0.1:8000/
```

### 6. Build Static Documentation

To verify and generate static HTML output locally:

```bash
mkdocs build -f docs-stack-material/mkdocs.yml --strict
```

---

## Deployment

### Automated Deployment (GitHub Actions)

Deployments are fully automated. Any commit pushed to the `main` branch automatically triggers `.github/workflows/docs.yml`, which installs dependencies, builds the documentation with the correct configuration (`docs-stack-material/mkdocs.yml`), and publishes to the `gh-pages` branch.

### Manual Deployment (CLI)

To manually push a build to GitHub Pages from your terminal:

```bash
mkdocs gh-deploy --config-file docs-stack-material/mkdocs.yml --force
```

---

## Author & License

- **Author**: Ashif E.K ([ashifek.in](https://ashifek.in))
- **License**: MIT
