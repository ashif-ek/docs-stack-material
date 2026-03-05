# Portfolio — Modern React & PWA

## 1. Project Overview

The **Personal Portfolio** is a high-performance, progressive web application (PWA) engineered to showcase professional work with a premium aesthetic. Built with the React 18 ecosystem, it features a glassmorphism UI, complex animations, and a simulated backend infrastructure for content management.

Unlike static portfolios, this project implements a **dynamic content management system** using a custom Node.js server, allowing for real-time updates to projects and skills without code deployment.

## 2. Core Architecture

### Architectural Pattern

**Backend-for-Frontend (BFF) Simulation**

The application uses a hybrid architecture:
*   **Client**: Single Page Application (SPA) with client-side routing.
*   **Server**: A custom Node.js/Express-like layer wrapping JSON Server.
*   **State**: Local persistence synchronized with server state.

### Key Technical Features

*   **PWA Compliance**: Installable on native devices with offline capability.
*   **Dynamic Theming**: System-preference aware dark/light mode with robust context management.
*   **Admin Layer**: Secured dashboard for content CRUD operations.

## 3. Technology Stack

### Frontend Engineering

*   **Core**: React 18, Vite 5
*   **Styling Engine**: Tailwind CSS 4 (Atomic CSS)
*   **Motion**: Framer Motion (Physics-based animations)
*   **Navigation**: React Router DOM 6.4 (Data routers)
*   **Icons**: Lucide React (Tree-shakable)

### Backend & Data

*   **Runtime**: Node.js
*   **API Layer**: JSON Server (Custom Middleware)
*   **File Handling**: Multer (Multipart/form-data)
*   **Persistence**: JSON-based NoSQL simulation

## 4. UI/UX Engineering

### 4.1 Glassmorphism & Aesthetics

The design system implements a modern "Glass" aesthetic:
*   **Backdrop Filters**: Heavy use of `backdrop-blur` for depth checks.
*   **Responsive Gradients**: Dynamic background meshes that react to scroll.

### 4.2 Interaction Design

*   **Micro-interactions**: Hover states, button presses, and loading skeletons.
*   **Page Transitions**: AnimatePresence implementation for smooth route changes.

## 5. System Functions

### Admin Dashboard
A protected route (`/admin`) allows for:
*   **Project Management**: upload images, set stack tags, update descriptions.
*   **Analytics**: View visit counts (simulated).
*   **Security**: Basic auth gate for admin routes.

### Contact System
*   **Integration**: Formspree API for serverless form handling.
*   **Validation**: Client-side schema validation before submission.

## 6. Performance Optimization

*   **Bundle Splitting**: Route-based code splitting via `React.lazy`.
*   **Asset Optimization**: WebP format for all portfolio imagery.
*   **Atomic CSS**: Tailwind ensures CSS bundle size remains constant regardless of app size.
*   **PWA Caching**: Service workers cache static assets for instant load on repeat visits.

## 7. Installation

### Development Environment

```bash
git clone https://github.com/ashif-ek/portfolio-react.git
cd portfolio-react
```

**1. Start Backend Server**
```bash
cd server
npm install
# Creates local server at port 5000
npm start
```

**2. Start React Client**
```bash
cd client
npm install
npm run dev
```

## 8. Deployment Strategy

*   **Frontend**: Deployed to Vercel (Edge Network).
    *   *Correction*: Uses Vercel's rewrite rules for SPA routing.
*   **Backend**: Deployed to Render.com.
    *   *Health Checks*: Implemented to prevents cold-start timeouts.

## 9. Summary

This portfolio represents a **Systematic approach to frontend development**, prioritizing:
1.  **Maintainability**: Component-driven architecture.
2.  **Scalability**: Externalized data layer.
3.  **User Experience**: Native-like feel via PWA and animations.
