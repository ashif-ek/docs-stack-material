# Personal Portfolio Website

A modern, responsive, and feature-rich personal portfolio website built with React, Vite, and Node.js. Designed to showcase projects, skills, and professional experience with a premium aesthetic and seamless user experience.

## 🚀 Features

*   **Modern UI/UX**: Built with Tailwind CSS v4 and Framer Motion for smooth animations and glassmorphism effects.
*   **Theme Support**: Fully integrated Dark and Light modes with persistent state.
*   **Admin Dashboard**: Secure admin panel to manage content, view stats, and upload files.
*   **Dynamic Content**: Backend powered by JSON Server with custom middleware for easy content management.
*   **Image Uploads**: Custom file upload functionality with Multer.
*   **Contact Integration**: Formspree integration for contact form submissions.
*   **Responsive Design**: Fully responsive layout optimized for Mobile, Tablet, and Desktop.
*   **PWA Ready**: Configured with Vite PWA plugin for installable app-like experience.

## 🛠️ Tech Stack

### Frontend
*   **Framework**: React 18
*   **Build Tool**: Vite
*   **Styling**: Tailwind CSS
*   **Animations**: Framer Motion
*   **Icons**: Lucide React, React Icons
*   **Charts**: Recharts
*   **Routing**: React Router

### Backend
*   **Runtime**: Node.js
*   **Server**: JSON Server (Custom Interface)
*   **File Handling**: Multer
*   **Database**: JSON Server

## 📦 Installation

Clone the repository:

```bash
git clone https://github.com/ashif-ek/portfolio-react.git
cd portfolio
```

### Frontend Setup

Navigate to the frontend directory:
```bash
cd my-app
```

Install dependencies:
```bash
npm install
```

Start the development server:
```bash
npm run dev
```

### Backend Setup

Navigate to the server directory:
```bash
cd server
```

Install dependencies:
```bash
npm install
```

Configure environment variables: Create a `.env` file in the server directory with the following:
```env
PORT=5000
ADMIN_USERNAME=admin
ADMIN_PASSWORD=your_secure_password
```

Start the server:
```bash
npm start
```

## 🚀 Deployment

### Frontend (Vercel)
The frontend is optimized for deployment on Vercel. Connect your repository and set the root directory to `my-app`.

### Backend (Render)
The backend is set up for Render. Ensure you set the Root Directory to `server` and add the environment variables in the Render dashboard.

[View on GitHub](https://github.com/ashif-ek/portfolio-react)
