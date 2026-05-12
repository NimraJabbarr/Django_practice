# Django Practice - School CRM System

Learn Django for deployment with a practical School CRM project.

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Installation](#installation)
- [Configuration](#configuration)
- [Running the Application](#running-the-application)
- [API Endpoints](#api-endpoints)
- [Database Models](#database-models)
- [Admin Panel](#admin-panel)
- [Deployment](#deployment)
- [Contributing](#contributing)
- [License](#license)
- [Contact & Support](#contact--support)

## 🎯 Overview

**Django_practice** is a comprehensive School Customer Relationship Management (CRM) system built with Django. This project demonstrates best practices for developing, structuring, and deploying Django applications in a production environment.

The system manages:
- Student information and enrollment
- Course and class management
- Teacher and staff records
- Attendance tracking
- Fee management
- Communication and notifications

## ✨ Features

- **User Authentication & Authorization** - Secure login with role-based access control
- **Student Management** - Complete student records with enrollment tracking
- **Course Management** - Organize courses, classes, and schedules
- **Attendance System** - Track student and staff attendance
- **Fee Management** - Manage fees, payments, and financial records
- **Admin Dashboard** - Comprehensive Django admin interface
- **RESTful API** - API endpoints for frontend integration
- **Database Optimization** - Efficient queries and indexing
- **Security Best Practices** - CSRF protection, password hashing, secure headers
- **Error Handling** - Comprehensive error logging and handling

## 🛠️ Tech Stack

| Component | Technology |
|-----------|-----------|
| **Backend Framework** | Django 4.x+ |
| **Programming Language** | Python 3.8+ |
| **Database** | SQLite (Development) / PostgreSQL (Production) |
| **ORM** | Django ORM |
| **API Framework** | Django REST Framework |
| **Authentication** | Django Authentication System |
| **Admin Interface** | Django Admin |
| **Task Queue** | Celery (optional) |
| **Web Server** | Gunicorn / uWSGI |
| **Server** | Nginx / Apache |

## 📁 Project Structure

```
Django_practice/
│
├── school_crm/                 # Main Django project folder
│   ├── __init__.py
│   ├── settings.py            # Project settings and configuration
│   ├── urls.py                # Main URL routing
│   ├── asgi.py                # ASGI configuration
│   ├── wsgi.py                # WSGI configuration
│   └── ...
│
├── apps/
│   ├── students/              # Student app
│   │   ├── models.py
│   │   ├── views.py
│   │   ├── urls.py
│   │   ├── serializers.py
│   │   ├── admin.py
│   │   └── ...
│   │
│   ├── courses/               # Course app
│   │   ├── models.py
│   │   ├── views.py
│   │   ├── urls.py
│   │   └── ...
│   │
│   ├── attendance/            # Attendance app
│   │   ├── models.py
│   │   ├── views.py
│   │   └── ...
│   │
│   └── accounts/              # User authentication app
│       ├── models.py
│       ├── views.py
│       └── ...
│
├── templates/                 # HTML templates
│   ├── base.html
│   ├── dashboard.html
│   └── ...
│
├── static/                    # Static files (CSS, JS, images)
│   ├── css/
│   ├── js/
│   └── images/
│
├── manage.py                  # Django management script
├── requirements.txt           # Python dependencies
├── .env.example              # Environment variables template
├── .gitignore                # Git ignore file
└── README.md                 # This file
```

## 🚀 Getting Started

### Prerequisites

Before you begin, ensure you have installed:
- Python 3.8 or higher
- pip (Python package manager)
- Git
- Virtual Environment (venv or virtualenv)

### Installation

1. **Clone the repository:**
```bash
git clone https://github.com/NimraJabbarr/Django_practice.git
cd Django_practice
```

2. **Create a virtual environment:**
```bash
# On Windows
python -m venv venv
venv\Scripts\activate

# On macOS/Linux
python3 -m venv venv
source venv/bin/activate
```

3. **Install dependencies:**
```bash
pip install -r requirements.txt
```

4. **Create environment variables file:**
```bash
cp .env.example .env
```

## ⚙️ Configuration

1. **Update settings.py** (if needed):
   - Set `DEBUG = True` for development
   - Configure `ALLOWED_HOSTS`
   - Add your database configuration

2. **Database Setup:**
```bash
python manage.py migrate
```

3. **Create a superuser:**
```bash
python manage.py createsuperuser
```

4. **Load sample data (optional):**
```bash
python manage.py loaddata fixtures/sample_data.json
```

## ▶️ Running the Application

1. **Start the development server:**
```bash
python manage.py runserver
```

2. **Access the application:**
   - Dashboard: `http://localhost:8000/`
   - Admin Panel: `http://localhost:8000/admin/`

3. **Stop the server:**
   - Press `Ctrl + C` in the terminal

## 📡 API Endpoints

### Students
- `GET /api/students/` - List all students
- `POST /api/students/` - Create a new student
- `GET /api/students/{id}/` - Get student details
- `PUT /api/students/{id}/` - Update student
- `DELETE /api/students/{id}/` - Delete student

### Courses
- `GET /api/courses/` - List all courses
- `POST /api/courses/` - Create a new course
- `GET /api/courses/{id}/` - Get course details
- `PUT /api/courses/{id}/` - Update course
- `DELETE /api/courses/{id}/` - Delete course

### Attendance
- `GET /api/attendance/` - List attendance records
- `POST /api/attendance/` - Mark attendance
- `GET /api/attendance/{id}/` - Get attendance details

## 📊 Database Models

### Student Model
```python
class Student(models.Model):
    first_name = CharField(max_length=100)
    last_name = CharField(max_length=100)
    email = EmailField(unique=True)
    phone = CharField(max_length=15)
    enrollment_date = DateField()
    courses = ManyToManyField(Course)
```

### Course Model
```python
class Course(models.Model):
    name = CharField(max_length=200)
    code = CharField(max_length=50, unique=True)
    description = TextField()
    instructor = ForeignKey(User)
    capacity = IntegerField()
```

### Attendance Model
```python
class Attendance(models.Model):
    student = ForeignKey(Student)
    date = DateField()
    status = CharField(choices=[('Present', 'P'), ('Absent', 'A')])
```

## 🔐 Admin Panel

Access the Django admin interface at `/admin/`:

1. Login with your superuser credentials
2. Manage:
   - Students and enrollment
   - Courses and schedules
   - Attendance records
   - User accounts and permissions
   - System settings

## 🌐 Deployment

### Production Checklist

- [ ] Set `DEBUG = False` in settings.py
- [ ] Update `ALLOWED_HOSTS` with your domain
- [ ] Generate a secure `SECRET_KEY`
- [ ] Configure static files with whitenoise or similar
- [ ] Set up PostgreSQL database
- [ ] Configure email backend
- [ ] Enable HTTPS/SSL
- [ ] Set up environment variables

### Deployment Steps

1. **Using Gunicorn:**
```bash
pip install gunicorn
gunicorn school_crm.wsgi:application --bind 0.0.0.0:8000
```

2. **Using Docker (optional):**
```bash
docker build -t django_practice .
docker run -p 8000:8000 django_practice
```

3. **Using Heroku:**
```bash
heroku create your-app-name
git push heroku main
```

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Code Style

- Follow PEP 8 guidelines
- Use meaningful variable and function names
- Add docstrings to functions and classes
- Write tests for new features

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 📞 Contact & Support

- **Author:** NimraJabbarr
- **GitHub:** [NimraJabbarr](https://github.com/NimraJabbarr)
- **Repository:** [Django_practice](https://github.com/NimraJabbarr/Django_practice)

For questions, issues, or suggestions:
- Open an issue on GitHub
- Check existing documentation
- Review the code comments

---

**Happy Learning! 🚀**

*Last Updated: May 12, 2026*
