# Fullstack Blog JWT Docker

A robust, production-ready Blog Application that bridges a high-performance Django backend with a dynamic React frontend. This project demonstrates a complete full-stack workflow, featuring secure authentication, containerized deployment, and a modern responsive UI.

## 🚀 Key Features

*   **Secure Authentication**: Robust implementation of JWT (JSON Web Tokens) with access and refresh token rotation.
*   **Containerization**: Fully Dockerized environment using `docker-compose` for seamless orchestration of Backend (Django), Frontend (Vite), and Database (PostgreSQL).
*   **Modern Frontend**: Built with React 18 and Vite for lightning-fast HMR and build performance.
*   **Responsive UI**: Styled with Tailwind CSS for a mobile-first, clean aesthetic.
*   **RESTful API**: Well-structured API endpoints built with Django REST Framework (DRF).
*   **CRUD Operations**: Complete management of Blog Posts, including creation, editing, deleting, and viewing.

## 🛠️ Tech Stack

### Backend
*   **Framework**: Django 4+ & Django REST Framework
*   **Authentication**: Simple JWT
*   **Database**: PostgreSQL
*   **Containerization**: Docker & Docker Compose

### Frontend
*   **Framework**: React 18
*   **Build Tool**: Vite
*   **Styling**: Tailwind CSS
*   **State Management**: React Context / Hooks
*   **HTTP Client**: Axios with Interceptors (for auto-token refresh)

## 📦 Installation & Setup

### Option 1: Docker (Recommended)

Run the entire stack with a single command.

1.  **Clone the repository**:
    ```bash
    git clone https://github.com/ashif-ek/fullstack-blog-jwt-docker.git
    cd fullstack-blog-jwt-docker
    ```

2.  **Start Services**:
    ```bash
    docker-compose up --build
    ```

    *   **Frontend**: http://localhost:5173
    *   **Backend API**: http://localhost:8000/api
    *   **Admin Panel**: http://localhost:8000/admin

### Option 2: Manual Setup

#### Backend
1.  Navigate to `backend/`:
    ```bash
    cd backend
    python -m venv venv
    source venv/bin/activate  # Windows: venv\Scripts\activate
    pip install -r requirements.txt
    ```
2.  Run Migrations & Server:
    ```bash
    python manage.py migrate
    python manage.py runserver
    ```

#### Frontend
1.  Navigate to `frontend/`:
    ```bash
    cd frontend
    npm install
    ```
2.  Start Dev Server:
    ```bash
    npm run dev
    ```

## 🔐 API Endpoints

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `POST` | `/api/token/` | Obtain Access & Refresh Tokens |
| `POST` | `/api/token/refresh/` | Refresh Access Token |
| `GET` | `/api/posts/` | List all blog posts |
| `POST` | `/api/posts/` | Create a new post (Auth required) |
| `GET` | `/api/posts/<id>/` | Retrieve a single post |
| `PUT` | `/api/posts/<id>/` | Update a post (Owner only) |

## 🏗️ Docker Architecture

The `docker-compose.yml` orchestrates three main services:
1.  **db**: PostgreSQL database.
2.  **backend**: Django API (depends on `db`).
3.  **frontend**: React App (depends on `backend`).

This ensures that the database is ready before the backend starts, and the backend is up before the frontend tries to connect.

[View on GitHub](https://github.com/ashif-ek/fullstack-blog-jwt-docker)
