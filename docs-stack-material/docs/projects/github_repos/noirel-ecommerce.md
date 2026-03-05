# NOIREL — Full-Stack Luxury E-Commerce Platform

## 1. Project Overview

Noirel is a production-grade, headless e-commerce platform engineered to deliver a high-performance luxury shopping experience. The system separates frontend and backend concerns using a modern React-based client and a secure Django REST API backend.

The architecture emphasizes:

*   **Scalability**
*   **Performance optimization**
*   **Secure authentication**
*   **Cloud-native deployment**
*   **Clean system design**
*   **Real-world payment processing**

It replicates modern commerce infrastructure used in industry-level platforms.

## 2. Core Architecture

### Architectural Pattern

**Headless Architecture (Decoupled Client–Server)**

Frontend and backend communicate strictly via REST APIs.

`Client (React) → Nginx → Gunicorn → Django → PostgreSQL`
                               `↓`
                              `AWS S3`

### Why Headless?

*   Independent scaling of frontend and backend
*   Deployment flexibility
*   Clean API contract
*   Frontend portability (future mobile app possible)

## 3. Technology Stack

### Frontend

*   **Framework**: React 19
*   **Build Tool**: Vite 6
*   **Styling**: Tailwind CSS 4
*   **Routing**: React Router 7
*   **State Management**: Context API (Auth, Cart, Wishlist, Search)
*   **HTTP Client**: Axios (JWT interceptors)
*   **Animation**: Framer Motion
*   **Charts**: Recharts
*   **Icons**: Lucide React
*   **PWA Support**: vite-plugin-pwa

**Key Frontend Design Decisions:**

*   Component isolation to reduce unnecessary re-renders
*   Route-based lazy loading
*   Memoized context values
*   Chunk splitting for caching efficiency
*   WebP image optimization
*   Mobile-first responsive design

### Backend

*   **Framework**: Django 5
*   **API**: Django REST Framework
*   **Authentication**: Simple JWT
*   **Database**: PostgreSQL
*   **Image Processing**: Pillow
*   **Payment Gateway**: Razorpay
*   **API Docs**: drf-spectacular
*   **Server**: Gunicorn

### Infrastructure

*   **Frontend Hosting**: Vercel (Global CDN)
*   **Backend Hosting**: AWS EC2 (Ubuntu)
*   **Reverse Proxy**: Nginx
*   **Media Storage**: AWS S3
*   **Database Hosting**: AWS RDS PostgreSQL
*   **CI/CD**: GitHub Actions

## 4. System Modules

### 4.1 Authentication Module

*   JWT-based authentication
*   Access + refresh token flow
*   Axios interceptor for auto token injection
*   Protected routes in frontend
*   Role-based access (Admin / User)

**Security Features:**

*   Strict CORS
*   Throttling on sensitive endpoints
*   Hashed passwords
*   Token validation middleware

### 4.2 Product Module

**Features:**

*   Product CRUD (Admin)
*   Category-based filtering
*   Search functionality
*   Best Sellers / New Arrivals logic
*   Stock tracking
*   Image upload to S3

**Database Optimization:**

*   Indexed fields (`is_active`, `created_at`)
*   Foreign key indexing
*   Efficient query selection

### 4.3 Cart System

Server-side persistent cart.

**Flow:**

1.  User adds item
2.  API validates stock
3.  Item stored in cart table
4.  Response updates UI

**Features:**

*   Quantity updates
*   Real-time sync
*   Prevent overstock ordering

### 4.4 Order & Checkout Module

**Multi-step Checkout:**

*   Address selection
*   Order summary
*   Payment initiation

**Order Creation:**

*   Atomic transaction
*   Stock validation
*   Total calculation
*   Payment signature verification

```python
with transaction.atomic():
    validate_stock()
    create_order()
    reduce_inventory()
```

Prevents race conditions and inconsistent state.

### 4.5 Payment Integration

*   **Gateway**: Razorpay

**Flow:**

1.  Order created server-side
2.  Payment order generated
3.  Client completes payment
4.  Signature verified server-side
5.  Order marked as paid

**Security:**

*   Server-side signature validation
*   Payment amount verification

### 4.6 Admin Dashboard

*   Revenue analytics (Recharts)
*   Order status distribution
*   Product management
*   Stock management
*   User control (block/unblock)

Optimized for operational control.

## 5. Performance Engineering

### Frontend Optimizations

1.  **Image Optimization**
    *   Converted assets to WebP
    *   Reduced payload size significantly
2.  **Code Splitting**
    *   Vite manual chunk configuration: `vendor`, `ui`, `charts`
    *   Improves caching and load performance.
3.  **Memoization Strategy**
    *   `useMemo` for context value
    *   Isolated modal component
    *   Avoided grid-wide re-renders
    *   Memoized sorting in OrderHistory
4.  **Lazy Loading**
    ```javascript
    const ProductPage = React.lazy(() => import('./ProductPage'));
    ```
    Improves initial load performance.

### Backend Optimizations

1.  **Database Indexing**
    *   Indexed: Foreign keys, `created_at`, `is_active`
    *   Reduces query scan time.
2.  **Atomic Transactions**
    *   Ensures: No partial order creation, No inconsistent stock updates
3.  **Rate Limiting**
    *   Applied throttling for: Auth endpoints, Sensitive actions

## 6. Database Design Overview

*   **Users**
    *   Custom user model
    *   Email as unique identifier
    *   Role flag
*   **Products**
    *   Name, Description, Price, Stock, Category, Image, `is_active`
*   **Cart**
    *   User, Product, Quantity
*   **Orders**
    *   User, Total, Status, Payment ID, Shipping info
*   **OrderItems**
    *   Order, Product, Quantity, Price snapshot

## 7. DevOps & Deployment

### Backend Deployment Flow

1.  Push to GitHub
2.  GitHub Actions triggered
3.  SSH into EC2
4.  Pull latest code
5.  Install dependencies
6.  Apply migrations
7.  Restart Gunicorn

### Nginx Responsibilities

*   Reverse proxy
*   HTTPS termination
*   Static file handling

### Why Gunicorn?

*   WSGI server optimized for production
*   Handles concurrency efficiently

## 8. Security Implementation

*   JWT authentication
*   Server-side payment verification
*   Rate limiting
*   Strict CORS
*   Environment-based secrets
*   Secure S3 storage
*   Database not exposed publicly
*   Nginx HTTPS configuration

## 9. Scalability Considerations

**Current scaling strategy:**

*   Decoupled frontend/backend
*   S3 media offloading
*   Indexed queries
*   Stateless JWT auth

**Future scaling options:**

*   Redis caching layer
*   Celery background workers
*   Horizontal EC2 scaling
*   Load balancer
*   CDN caching rules
*   Containerization with Docker

## 10. CI/CD Pipeline

**Automated:**

*   Code pull
*   Dependency install
*   Database migration
*   Gunicorn restart

Ensures zero manual deployment errors.

## 11. Lighthouse & UX Improvements

*   Near-perfect Lighthouse score
*   Accessible design
*   Responsive layout
*   Minimal layout shifts
*   Smooth animations
*   PWA installable capability

## 12. Future Roadmap

*   Email notifications (SendGrid / SES)
*   OAuth (Google login)
*   Recommendation engine
*   Advanced analytics dashboard
*   Redis integration
*   Celery task queue
*   Observability (logging + monitoring)

## 13. Engineering Principles Applied

*   Separation of concerns
*   API-first design
*   Atomicity
*   Query optimization
*   Component isolation
*   Clean UI state architecture
*   Cloud-native deployment

## 14. Summary

Noirel is not a simple CRUD application.

It demonstrates:

*   Full lifecycle engineering
*   Cloud deployment experience
*   Payment integration
*   Performance tuning
*   Security awareness
*   Real-world system architecture

It reflects practical understanding of modern full-stack development at production level.
