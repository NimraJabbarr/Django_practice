<div align="center">

# 🎓 Django Practice — School CRM System

### Learn Django the practical way — by building a real School CRM from scratch.

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python&logoColor=white)](https://www.python.org/)
[![Django](https://img.shields.io/badge/Django-4.x-092E20?logo=django&logoColor=white)](https://www.djangoproject.com/)
[![DRF](https://img.shields.io/badge/DRF-REST%20API-red)](https://www.django-rest-framework.org/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Production-336791?logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

</div>

---

## 📖 Overview

**Django_practice** is a comprehensive **School Customer Relationship Management (CRM)** system built with Django. This project demonstrates best practices for developing, structuring, and deploying Django applications in a production environment.

It's not just a tutorial — it's a **real-world project** that teaches you:

- How to structure a Django project properly
- How to build secure authentication with role-based access
- How to expose a clean REST API with Django REST Framework
- How to prepare a Django app for production deployment

The system manages:

- 👨‍🎓 **Student information and enrollment**
- 📚 **Course and class management**
- 👩‍🏫 **Teacher and staff records**
- 📋 **Attendance tracking**
- 💰 **Fee management**
- 📢 **Communication and notifications**

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [Tech Stack](#️-tech-stack)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [Configuration](#️-configuration)
- [Running the Application](#️-running-the-application)
- [API Endpoints](#-api-endpoints)
- [Database Models](#-database-models)
- [Admin Panel](#-admin-panel)
- [Deployment](#-deployment)
- [Contributing](#-contributing)
- [License](#-license)
- [Contact](#-contact)

---

## ✨ Features

- 🔐 **User Authentication & Authorization** — secure login with role-based access control
- 👨‍🎓 **Student Management** — complete student records with enrollment tracking
- 📚 **Course Management** — organize courses, classes, and schedules
- 📋 **Attendance System** — track student and staff attendance
- 💰 **Fee Management** — manage fees, payments, and financial records
- 🛡️ **Admin Dashboard** — comprehensive Django admin interface
- 🔌 **RESTful API** — clean endpoints for frontend integration
- ⚡ **Database Optimization** — efficient queries and indexing
- 🔒 **Security Best Practices** — CSRF protection, password hashing, secure headers
- 🚨 **Error Handling** — comprehensive logging and graceful failure

---

## 🛠️ Tech Stack

| Component | Technology |
|-----------|------------|
| **Backend Framework** | Django 4.x+ |
| **Language** | Python 3.8+ |
| **Database (Dev)** | SQLite |
| **Database (Prod)** | PostgreSQL |
| **ORM** | Django ORM |
| **API Framework** | Django REST Framework |
| **Authentication** | Django Auth System |
| **Admin Interface** | Django Admin |
| **Task Queue** | Celery _(optional)_ |
| **Web Server** | Gunicorn / uWSGI |
| **Reverse Proxy** | Nginx / Apache |

---

## 📁 Project Structure

```text
Django_practice/
│
├── school_crm/                 # Main Django project folder
│   ├── __init__.py
│   ├── settings.py             # Project settings & config
│   ├── urls.py                 # Main URL routing
│   ├── asgi.py                 # ASGI config
│   ├── wsgi.py                 # WSGI config
│   └── ...
│
├── apps/
│   ├── students/               # Student app
│   │   ├── models.py
│   │   ├── views.py
│   │   ├── urls.py
│   │   ├── serializers.py
│   │   ├── admin.py
│   │   └── ...
│   │
│   ├── courses/                # Course app
│   │   ├── models.py
│   │   ├── views.py
│   │   ├── urls.py
│   │   └── ...
│   │
│   ├── attendance/             # Attendance app
│   │   ├── models.py
│   │   ├── views.py
│   │   └── ...
│   │
│   └── accounts/               # User auth app
│       ├── models.py
│       ├── views.py
│       └── ...
│
├── templates/                  # HTML templates
│   ├── base.html
│   ├── dashboard.html
│   └── ...
│
├── static/                     # Static files (CSS, JS, images)
│   ├── css/
│   ├── js/
│   └── images/
│
├── manage.py                   # Django management script
├── requirements.txt            # Python dependencies
├── .env.example                # Environment variable template
├── .gitignore                  # Git ignore rules
└── README.md                   # You are here
