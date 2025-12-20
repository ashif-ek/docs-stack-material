# Architecture

The projects in this portfolio primarily adhere to modern web development architectures, ensuring scalability, maintainability, and performance.

## Frontend
*   **Component-Based**: Built mainly with React.js, emphasizing reusable UI components.
*   **State Management**: Utilizing Context API, Redux Toolkit, or Zustand depending on complexity.
*   **Styling**: Tailwind CSS is the standard for responsive and utility-first styling.

## Backend
*   **REST API**: Most backends (Django, FastAPI, Node.js) expose RESTful endpoints.
*   **MVC / MVT**: Django projects follow the Model-View-Template pattern (similar to MVC).
*   **Microservices vs Monolith**: Smaller tools (Time Lens) are microservices/functions, while larger platforms (Student Management, Noirel) are modular monoliths.

## Database
*   **Relational**: PostgreSQL is the preferred choice for complex data relations (Salary Checker, Student Management).
*   **NoSQL**: MongoDB or JSON Server is used for lighter or rapid-prototyping projects (Portfolio).

## Deployment
*   **Frontend**: Vercel / Netlify.
*   **Backend**: Render / Railway / Heroku.
*   **Containerization**: Docker is used to standardize runtime environments.