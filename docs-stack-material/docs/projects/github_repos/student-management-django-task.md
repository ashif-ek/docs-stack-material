# Student Management System (Django)

> **A comprehensive student management platform engineered with Django.**

This system delivers robust role-based functionality, featuring secure authentication, dedicated dashboards, course administration, and automated email notifications. It leverages Django's robust architectural patterns to ensure a clean, scalable, and maintainable codebase.

[View Repository on GitHub](https://github.com/ashif-ek/student-management-django-task){ .md-button .md-button--primary }

---

## ✨ Core Features

### Role-Based Architecture
- **Custom User Models**: Implements an extended Django AbstractUser to cleanly separate `Admin` and `Student` entities, paving the way for differentiated access and profiling.
- **Dedicated Dashboards**: Provides isolated UI environments tailored for administrators (managing users, courses, and system health) and students (accessing enrollments, schedules, and grades).

### Academic & Notification Systems
- **Course Management**: End-to-end CRUD (Create, Read, Update, Delete) operations for courses, subjects, and academic scheduling.
- **Email Notifications**: Integrated SMTP functionality to dispatch automated alerts for enrollments, password resets, and important administrative announcements.
- **Comprehensive CRUD Operations**: Full database interaction capabilities for all major platform models, protected by robust data validation and permission checks.

---

## 🛠️ Technology Stack

- **Backend Framework**: Django (Python)
- **Database**: SQLite (Development) / PostgreSQL (Production ready)
- **Frontend Template**: Django HTML Templates combined with static CSS and JS
- **Authentication**: Django's built-in Auth backend with Session Management
- **Mailing**: Django `django.core.mail` module integrated with standard SMTP interfaces

---

## 🏗️ Architectural Highlights

### Clean MVT Pattern
The application strictly follows Django's **Model-View-Template (MVT)** architecture:
1. **Models**: Defines the relational data structure specifically architected around customized abstract/base user models.
2. **Views**: Handles business logic, leveraging Django's Class-Based Views (CBVs) for reusability and DRY compliance. 
3. **Templates**: Renders dynamic, securely escaped UI elements utilizing the Django Template Language (DTL).

### Security Measures
- CSRF protection enabled on all unified forms.
- SQL Injection mitigation natively handled by Django's ORM.
- Proper view decorators (`@login_required`, custom permission decorators) guarding sensitive routes.

---

## 🏁 Installation & Setup

To deploy the platform in a local development environment:

1. **Clone the project:**
   ```bash
   git clone https://github.com/ashif-ek/student-management-django-task.git
   cd student-management-django-task
   ```

2. **Create and activate a virtual environment:**
   ```bash
   python -m venv venv
   # On Windows
   venv\Scripts\activate
   # On macOS/Linux
   source venv/bin/activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Apply database migrations:**
   ```bash
   python manage.py makemigrations
   python manage.py migrate
   ```

5. **Create a superuser (Admin):**
   ```bash
   python manage.py createsuperuser
   ```

6. **Run the development server:**
   ```bash
   python manage.py runserver
   ```

7. **Access the application:**
   Navigate to `http://127.0.0.1:8000/` in your web browser.
