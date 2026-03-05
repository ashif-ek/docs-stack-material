# Deployment & Release Strategies

This technical guide defines the deployment architecture and continuous delivery pipelines utilized to transition the portfolio's applications from local development into highly available production environments.

---

## ⚡ Global Edge Deployment (Frontend)

For JavaScript-heavy architectures, specifically Single Page Applications (SPAs) built with React and Vite, Edge deployment networks like **Vercel** or **Netlify** are strictly utilized.

### Vercel Deployment Protocol
1.  **VCS Integration**: Authenticate and bind your Vercel account directly to the target GitHub repository.
2.  **Continuous Deployment Configuration**:
    *   **Framework Preset**: Select `Vite` or `Next.js` (Vercel typically auto-detects this based on `package.json`).
    *   **Build Command**: `npm run build`
    *   **Output Directory**: Ensure this maps to `dist` (Vite) or `.next` (Next.js).
3.  **Secret Management**: Inject all necessary variables from your local `.env.production` directly into the Vercel Environment Variables dashboard prior to initiating the primary build.

---

## ☁️ Platform-as-a-Service (Backend)

For stateful API servers constructed in Python (Django, FastAPI) or Node.js, managed container environments like **Render** or **Railway** ensure high uptime without the operational overhead of managing bare-metal servers.

### Render Web Service Protocol
1.  **Service Instantiation**: Create a new "Web Service" tied to the backend repository branch (e.g., `main`).
2.  **Runtime Specifications**: Define the native environment (e.g., `Python 3` or `Node`).
3.  **Build Phase Definition**:
    *   *Python*: `pip install -r requirements.txt && python manage.py migrate`
    *   *Node*: `npm install`
4.  **Execution Commands (Start)**:
    *   *FastAPI (Production ASGI)*: `uvicorn main:app --host 0.0.0.0 --port $PORT`
    *   *Django (Production WSGI)*: `gunicorn core.wsgi:application`

---

## 🐳 Docker Orchestration

For environments demanding absolute parity, or applications involving complex microservice interactions (e.g., the `fullstack-blog-jwt-docker`), we deploy using Docker Native tooling.

### Standard Container Build Pipeline
```bash
# Compile the immutable Docker image, tagging it appropriately
docker build -t ashif-ek/my-app:latest .

# Instantiate the container, mapping the internal application port to the host
docker run -d -p 8000:8000 --name my-app-instance ashif-ek/my-app:latest
```

> **Note on Container Registries**: In a full CI/CD pipeline, these images are typically pushed to Docker Hub or AWS ECR before being pulled down to the production host.