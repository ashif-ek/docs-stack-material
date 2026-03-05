# Technical Glossary

This glossary aims to clarify the specialized technical terminology, acronyms, and architectural concepts utilized throughout the documentation and overarching project repositories. 

---

## A

**API (Application Programming Interface)**
A set of defined rules and protocols that allow different software applications to communicate with each other. In modern web development, this typically refers to a RESTful or GraphQL web API over HTTP.

**ASGI (Asynchronous Server Gateway Interface)**
A spiritual successor to WSGI, designed to provide a standard interface between async-capable Python web servers, frameworks (like FastAPI), and applications.

---

## C

**CRUD (Create, Read, Update, Delete)**
The four basic operations of persistent storage. It represents the foundational interactions any standard database-driven application requires.

**CSRF (Cross-Site Request Forgery)**
A type of malicious exploit whereby unauthorized commands are transmitted from a user that the web application trusts. Modern frameworks (like Django) mitigate this via synchronized token patterns.

---

## H

**Hook (React)**
Specialized JavaScript functions introduced in React 16.8 that allow functional components to "hook into" React state and lifecycle features (e.g., `useState`, `useEffect`) without writing a Class component.

**HMR (Hot Module Replacement)**
A critical developer experience (DX) feature in tools like Vite and Webpack that updates modules in the browser dynamically at runtime without necessitating a full page refresh.

---

## J

**JWT (JSON Web Token)**
An open, industry-standard (RFC 7519) method for securely transmitting information between parties as a JSON object. This information can be verified and trusted because it is digitally signed. Heavily utilized for stateless API authentication.

---

## M

**MVT (Model-View-Template)**
The specific software design pattern implemented natively by the Django framework.
- **Model**: Manages data logic and database schema mappings.
- **View**: Contains the business logic, processing requests and formulating responses.
- **Template**: The presentation layer responsible for dynamically generating HTML outputs.

---

**ORM (Object-Relational Mapping)**
A programming technique that maps application objects to relational database tables. This abstraction allows developers to query and manipulate data using an object-oriented paradigm (e.g., Python/Django ORM, SQLAlchemy) rather than writing raw SQL statements.

---

## S

**SPA (Single Page Application)**
A web application or website that interacts with the browser by dynamically rewriting the current web page with new data from the web server, instead of the default method of a web browser loading entire new pages. React is commonly used to build SPAs.

**SSR (Server-Side Rendering)**
The capability of an application to generate the HTML for a webpage on the server rather than in the browser. It is incredibly beneficial for Search Engine Optimization (SEO) and initial page load performance metrics.