# Deployment Strategies

This guide outlines how to deploy the various applications in this portfolio.

## Frontend Deployment (Vercel)

Most React/Next.js frontends are optimized for [Vercel](https://vercel.com).

1.  **Connect GitHub**: detailed instructions...
2.  **Import Project**: Select the repository.
3.  **Build Settings**:
    *   Framework Preset: `Vite` or `Next.js`
    *   Build Command: `npm run build`
    *   Output Directory: `dist` or `.next`
4.  **Environment Variables**: copy from your local `.env`.

## Backend Deployment (Render)

[Render](https://render.com) is the preferred choice for Python and Node.js backends.

1.  **Create Web Service**.
2.  **Connect Repo**.
3.  **Runtime**: `Python 3` or `Node`.
4.  **Build Command**:
    *   Python: `pip install -r requirements.txt`
    *   Node: `npm install`
5.  **Start Command**:
    *   FastAPI: `uvicorn main:app --host 0.0.0.0 --port $PORT`
    *   Django: `gunicorn core.wsgi:application`

## Docker Deployment

For containerized apps (like `fullstack-blog-jwt-docker`), use the `Dockerfile`:

```bash
docker build -t my-app .
docker run -p 8000:8000 my-app
```