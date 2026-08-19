# HealthSphere 🩺

> An AI-driven health and wellness platform designed to bring personalized health guidance, nutrition support, wellness planning, mindfulness resources, and user authentication into one digital ecosystem.

[![Django](https://img.shields.io/badge/Django-5.0-0C4B33?logo=django\&logoColor=white)](https://www.djangoproject.com/)
[![Python](https://img.shields.io/badge/Python-3.x-3776AB?logo=python\&logoColor=white)](https://www.python.org/)
[![Bootstrap](https://img.shields.io/badge/Bootstrap-5-7952B3?logo=bootstrap\&logoColor=white)](https://getbootstrap.com/)
[![JavaScript](https://img.shields.io/badge/JavaScript-ES6%2B-F7DF1E?logo=javascript\&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

---

## 📌 Table of Contents

* [Project Overview](#-project-overview)
* [Problem Statement](#-problem-statement)
* [Objectives](#-objectives)
* [Key Features](#-key-features)
* [System Architecture](#-system-architecture)
* [Technology Stack](#-technology-stack)
* [Project Structure](#-project-structure)
* [Main Django Application](#-main-django-application)
* [AI Health Assistant](#-ai-health-assistant)
* [Authentication System](#-authentication-system)
* [Calorie & Nutrition Finder](#-calorie--nutrition-finder)
* [Health & Wellness Modules](#-health--wellness-modules)
* [Application Routes](#-application-routes)
* [Installation](#-installation)
* [Environment Variables](#-environment-variables)
* [Running the Application](#-running-the-application)
* [API Integration](#-api-integration)
* [Security](#-security)
* [Current Project Status](#-current-project-status)
* [Future Enhancements](#-future-enhancements)
* [Credits](#-credits)
* [License](#-license)
* [Author](#-author)

---

# 🌐 Project Overview

**HealthSphere** is a web-based health and wellness platform that aims to make everyday health management easier through a centralized digital environment.

The project combines a responsive frontend with Django-powered backend modules and external API integrations.

HealthSphere focuses on several areas of personal wellness:

* 🤖 AI-powered health assistance
* 🥗 Nutrition and calorie information
* 🏃 Exercise and fitness
* 🧘 Meditation and mindfulness
* 😴 Sleep and relaxation
* 🧠 Mental health awareness
* 💧 Hydration management
* 📅 Daily wellness planning
* 🔐 User authentication
* 📚 Health articles and resources

The main landing page describes HealthSphere as an AI-driven health platform providing personalized insights, tracking tools, and interactive features.

---

# ❗ Problem Statement

People often use different applications for different aspects of their health.

For example:

* One application may track nutrition.
* Another may provide meditation content.
* Another may provide exercise guidance.
* Another may provide AI-based assistance.
* Another may be used for planning daily activities.

This fragmented experience can make it difficult for users to manage their overall wellness.

### HealthSphere addresses this problem by providing a centralized platform where users can access multiple health and wellness services through one application.

---

# 🎯 Objectives

The main objectives of HealthSphere are:

1. Provide a centralized health and wellness platform.
2. Provide AI-assisted responses to user health-related questions.
3. Help users understand nutrition and calorie information.
4. Provide resources for exercise and physical wellness.
5. Encourage mindfulness and meditation.
6. Provide sleep and mental-health resources.
7. Support daily wellness planning.
8. Provide hydration-related reminders and tracking concepts.
9. Implement secure user authentication.
10. Create a responsive and user-friendly interface.
11. Integrate external APIs where required.
12. Provide a scalable foundation for future health-tracking features.

---

# ✨ Key Features

## 🤖 1. AI Health Assistant

HealthSphere includes an AI assistant that allows users to submit prompts and receive AI-generated responses.

The Django backend communicates with the **WorqHat AI API**.

The implementation:

1. Receives a POST request.
2. Validates the JSON request.
3. Extracts the user's prompt.
4. Reads the API key from environment variables.
5. Sends the prompt to the WorqHat API.
6. Receives the AI-generated response.
7. Returns the response to the frontend.

The AI endpoint is implemented in:

```text
HealthSpehre/Health/myapp/views.py
```

The route is:

```text
/generate/
```

The current implementation uses the WorqHat Content API with the `aicon-v4-nano-160824` model.

---

# 🔐 2. User Authentication

HealthSphere uses Django's built-in authentication framework.

The authentication functionality includes:

* User registration
* Username validation
* Email validation
* Password validation
* Login
* Logout
* Session-based authentication
* Protected pages

### Registration

Users provide:

* First name
* Last name
* Username
* Email
* Password

The system checks whether the username or email already exists before creating an account.

### Login

Users authenticate using:

```text
Username
Password
```

Django's built-in authentication system verifies the credentials.

### Logout

Users can terminate their authenticated session using the logout endpoint.

---

# 🥗 3. Calorie & Nutrition Finder

HealthSphere contains a dedicated **Calorie Finder** Django module.

The module allows a user to enter a food item and retrieve nutritional information.

It uses the:

**API Ninjas Nutrition API**

The request flow is:

```text
User enters food
       ↓
Django View
       ↓
API Ninjas Nutrition API
       ↓
Nutrition JSON Response
       ↓
Django Template
       ↓
Nutrition Information
```

The implementation is located in:

```text
HealthSpehre/Calorie_Finder/
```

The main logic is handled by:

```text
HealthSpehre/Calorie_Finder/counter/views.py
```

The view sends the food query to the nutrition API and processes the returned JSON data.

---

# 🧘 Health & Wellness Modules

The HealthSphere interface contains multiple wellness-oriented modules.

## 🏃 Exercise

Provides an area dedicated to exercise and physical activity.

Route:

```text
/exercise/
```

---

## 🧘 Meditation

Provides meditation-related resources and content.

Route:

```text
/meditation/
```

---

## 🧠 Mindfulness

Provides mindfulness and relaxation-oriented content.

Route:

```text
/mindfulness/
```

---

## 😴 Sleep

Provides a dedicated section for sleep-related wellness information.

Route:

```text
/sleep/
```

---

## 🧠 Mental Health

Provides a dedicated section for mental-health-related resources.

Route:

```text
/mental-health/
```

---

## 💧 Hydration

HealthSphere includes a hydration-reminder feature concept designed to encourage users to maintain regular water intake.

The main website describes hydration reminders as a feature that tracks water intake and reminds users to stay hydrated throughout the day.

---

## 📅 Daily Planner

The Daily Planner is designed to help users organize wellness activities such as:

* Workouts
* Meals
* Mindfulness activities
* Daily health routines

The feature is presented as part of the HealthSphere frontend experience.

---

## 📊 Smart Health Tracking

The HealthSphere interface includes a smart health-tracking concept covering areas such as:

* Mood
* Calorie intake
* Fitness progress
* Sleep quality

This provides a foundation for future user-specific health analytics and dashboards.

---

# 🏗️ System Architecture

The project currently consists of a frontend website and several Django-based modules.

```text
                         ┌───────────────────────┐
                         │      User / Client    │
                         └───────────┬───────────┘
                                     │
                                     ▼
                         ┌───────────────────────┐
                         │ HealthSphere Frontend │
                         │ HTML / CSS / JS       │
                         │ Bootstrap             │
                         └───────────┬───────────┘
                                     │
                                     ▼
                         ┌───────────────────────┐
                         │    Django Backend     │
                         │      Python 3.x       │
                         └───────────┬───────────┘
                                     │
                  ┌──────────────────┼──────────────────┐
                  │                  │                  │
                  ▼                  ▼                  ▼
        ┌─────────────────┐ ┌────────────────┐ ┌─────────────────┐
        │ Authentication  │ │ AI Assistant   │ │ Nutrition API   │
        │ Django Auth     │ │ WorqHat AI     │ │ API Ninjas      │
        └─────────────────┘ └────────────────┘ └─────────────────┘
                  │                  │                  │
                  └──────────────────┼──────────────────┘
                                     │
                                     ▼
                           ┌───────────────────┐
                           │   User Response   │
                           └───────────────────┘
```

---

# 🧰 Technology Stack

## Frontend

| Technology                        | Purpose                    |
| --------------------------------- | -------------------------- |
| HTML5                             | Page structure             |
| CSS3                              | Styling                    |
| JavaScript                        | Client-side functionality  |
| Bootstrap 5                       | Responsive UI              |
| Bootstrap Icons                   | Icons                      |
| Font Awesome                      | UI icons                   |
| Owl Carousel                      | Carousel/slider components |
| Animate.css / animation libraries | UI animations              |

The main frontend uses Bootstrap stylesheets, Font Awesome, Bootstrap Icons, Owl Carousel, and animation libraries.

---

## Backend

| Technology            | Purpose                      |
| --------------------- | ---------------------------- |
| Python                | Backend programming          |
| Django 5.0            | Web framework                |
| Django ORM            | Database abstraction         |
| Django Authentication | User management              |
| Django Templates      | Server-side rendering        |
| SQLite                | Default development database |

The main Django project was generated using Django 5.0 and is configured with SQLite by default.

---

## External APIs

| API                      | Purpose                       |
| ------------------------ | ----------------------------- |
| WorqHat AI API           | AI-generated health responses |
| API Ninjas Nutrition API | Nutrition information         |

---

## Python Libraries

The Django AI example currently specifies:

```text
Django==5.0
python-dotenv==1.0.0
requests==2.31.0
```

---

# 📁 Project Structure

The repository contains the main frontend along with Django applications and supporting modules.

```text
HealthSphere/
│
├── README.md
├── LICENSE.txt
├── READ-ME.txt
├── 404.html
├── index.html
├── about.html
├── contact.html
├── facility.html
├── appointment.html
├── classes.html
├── call-to-action.html
│
├── css/
│   ├── bootstrap.min.css
│   └── style.css
│
├── js/
│   └── JavaScript files
│
├── img/
│   └── Images and visual assets
│
├── lib/
│   └── Third-party frontend libraries
│
└── HealthSpehre/
    │
    ├── Health/
    │   │
    │   ├── manage.py
    │   │
    │   ├── Health/
    │   │   ├── settings.py
    │   │   ├── urls.py
    │   │   ├── asgi.py
    │   │   └── wsgi.py
    │   │
    │   └── myapp/
    │       ├── views.py
    │       ├── urls.py
    │       ├── models.py
    │       └── templates/
    │
    ├── Calorie_Finder/
    │   │
    │   ├── manage.py
    │   ├── counter/
    │   │   ├── views.py
    │   │   ├── models.py
    │   │   ├── urls.py
    │   │   └── templates/
    │   │
    │   └── Static_foodie_html/
    │
    ├── Django Example/
    │   ├── manage.py
    │   ├── requirements.txt
    │   ├── README.md
    │   └── .env.example
    │
    ├── authentication/
    │   ├── AuthenticationProject/
    │   ├── Core/
    │   ├── templates/
    │   ├── static/
    │   └── manage.py
    │
    └── meditation/
```

The repository contains separate Django projects/modules for the health application, calorie finder, authentication work, and AI integration example.

---

# 🐍 Main Django Application

The primary Django application is located at:

```text
HealthSpehre/Health/
```

The Django project contains:

```text
manage.py
```

and the project configuration:

```text
Health/
├── settings.py
├── urls.py
├── wsgi.py
└── asgi.py
```

The application itself is:

```text
myapp/
```

The main application uses Django's built-in authentication system and exposes the HealthSphere pages and AI API.

---

# 🔗 Application Routes

The main Django application currently contains routes for the major HealthSphere modules.

| Route                      | Description            |
| -------------------------- | ---------------------- |
| `/`                        | Home page              |
| `/categories/`             | Health categories      |
| `/exercise/`               | Exercise               |
| `/category01/`             | Health category 1      |
| `/category02/`             | Health category 2      |
| `/category03/`             | Health category 3      |
| `/category04/`             | Health category 4      |
| `/articles-and-resources/` | Articles and resources |
| `/meditation/`             | Meditation             |
| `/sleep/`                  | Sleep                  |
| `/mindfulness/`            | Mindfulness            |
| `/mental-health/`          | Mental health          |
| `/plans/`                  | Wellness plans         |
| `/for-business/`           | Business section       |
| `/about/`                  | About HealthSphere     |
| `/help/`                   | Help                   |
| `/login/`                  | User login             |
| `/register/`               | User registration      |
| `/logout/`                 | Logout                 |
| `/index2/`                 | Authenticated page     |
| `/ai_index/`               | AI assistant interface |
| `/generate/`               | AI response API        |
| `/admin/`                  | Django admin           |

---

# 🤖 AI Health Assistant

## Architecture

The AI assistant follows this workflow:

```text
┌──────────────────┐
│ User enters      │
│ health question  │
└────────┬─────────┘
         │
         ▼
┌──────────────────┐
│ HealthSphere UI  │
└────────┬─────────┘
         │
         │ POST /generate/
         ▼
┌──────────────────┐
│ Django Backend   │
└────────┬─────────┘
         │
         ├── Validate JSON
         ├── Validate prompt
         └── Load API key
                  │
                  ▼
        ┌───────────────────┐
        │   WorqHat AI API  │
        └─────────┬─────────┘
                  │
                  ▼
        ┌───────────────────┐
        │ AI Generated Text │
        └─────────┬─────────┘
                  │
                  ▼
        ┌───────────────────┐
        │ Django JSON Reply │
        └─────────┬─────────┘
                  │
                  ▼
        ┌───────────────────┐
        │ HealthSphere UI   │
        └───────────────────┘
```

---

## AI API Request

The backend expects a JSON request similar to:

```json
{
  "prompt": "How can I improve my sleep?"
}
```

The backend validates the request before sending it to the external AI service.

---

## AI API Response

The Django endpoint returns information such as:

```json
{
  "content": "...",
  "processingTime": 0,
  "processingId": "...",
  "processingCount": 0,
  "conversation_id": "...",
  "model": "..."
}
```

These fields are taken from the WorqHat response when available.

---

# 🔐 Authentication System

The authentication workflow is implemented using Django's built-in authentication framework.

## Registration Flow

```text
User
 │
 ▼
Registration Form
 │
 ├── First Name
 ├── Last Name
 ├── Username
 ├── Email
 └── Password
 │
 ▼
Validation
 │
 ├── Username exists?
 ├── Email exists?
 └── Password length valid?
 │
 ▼
Django User Model
 │
 ▼
Account Created
 │
 ▼
Login
```

---

## Login Flow

```text
User
 │
 ▼
Login Form
 │
 ├── Username
 └── Password
 │
 ▼
Django authenticate()
 │
 ├── Valid ───────► Login
 │
 └── Invalid ─────► Error Message
```

---

## Protected Pages

The project uses Django's:

```python
@login_required
```

decorator to restrict authenticated pages.

---

# 🥗 Calorie Finder Architecture

The Calorie Finder is implemented as a separate Django module.

```text
HealthSpehre/
└── Calorie_Finder/
    └── counter/
        ├── views.py
        ├── models.py
        ├── urls.py
        └── templates/
```

The view uses the API Ninjas nutrition endpoint to retrieve nutritional information for a food query.

---

# ⚙️ Installation

## 1. Clone the Repository

```bash
git clone https://github.com/ThePranish03/HealthSphere.git
```

Navigate into the project:

```bash
cd HealthSphere
```

---

# 🐍 2. Create Virtual Environment

Navigate to the main Django project:

```bash
cd HealthSpehre/Health
```

Create a virtual environment:

```bash
python -m venv venv
```

---

# 🪟 Windows

Activate:

```bash
venv\Scripts\activate
```

---

# 🐧 macOS / Linux

Activate:

```bash
source venv/bin/activate
```

---

# 📦 3. Install Dependencies

Install the required packages:

```bash
pip install django python-dotenv requests
```

Alternatively, if using the provided AI example requirements:

```bash
pip install -r "../Django Example/requirements.txt"
```

The repository's Django example specifies Django 5.0, `python-dotenv`, and `requests`.

---

# 🗄️ 4. Run Database Migrations

From:

```text
HealthSpehre/Health/
```

run:

```bash
python manage.py migrate
```

---

# 👤 5. Create Superuser

To access the Django administration panel:

```bash
python manage.py createsuperuser
```

Follow the prompts to create an administrator account.

---

# ▶️ 6. Start Development Server

```bash
python manage.py runserver
```

Open:

```text
http://127.0.0.1:8000/
```

---

# 🔑 Environment Variables

The AI integration uses environment variables rather than hardcoding credentials in the Django settings.

Create a `.env` file:

```env
DJANGO_SECRET_KEY=your_secret_key_here
WORQHAT_API_KEY=your_worqhat_api_key_here
```

The Django settings load environment variables using `python-dotenv`.

---

# ⚠️ Important Security Warning

**Never commit real API keys or secret credentials to GitHub.**

The repository currently contains a credential inside:

```text
HealthSpehre/Django Example/.env.example
```

That credential should be considered exposed and should be **revoked/rotated immediately**.

For a secure project, `.env` should contain local secrets while `.gitignore` should prevent it from being committed.

Example:

```gitignore
.env
*.sqlite3
__pycache__/
*.pyc
venv/
```

---

# 🔌 API Integration

HealthSphere currently integrates external APIs for two major capabilities.

## WorqHat AI

Used for:

```text
AI-generated responses
```

The backend communicates with:

```text
https://api.worqhat.com/api/ai/content/v4
```

---

## API Ninjas

Used for:

```text
Food nutrition information
```

The Calorie Finder sends a food query to the API Ninjas nutrition endpoint and processes the returned JSON response.

---

# 🔄 Overall Application Flow

```text
                     HEALTHSPHERE
                          │
                          ▼
                ┌───────────────────┐
                │   Web Interface   │
                └─────────┬─────────┘
                          │
          ┌───────────────┼───────────────┐
          │               │               │
          ▼               ▼               ▼
     Authentication   AI Assistant   Health Modules
          │               │               │
          ▼               ▼               ▼
     Django Auth      WorqHat API     Django Views
          │               │               │
          │               │        ┌──────┼──────┐
          │               │        │      │      │
          │               │        ▼      ▼      ▼
          │               │     Exercise Sleep Meditation
          │               │
          │               ▼
          │          AI Response
          │
          ▼
     User Session
```

---

# 📊 Feature Matrix

| Feature                   | Status | Technology              |
| ------------------------- | ------ | ----------------------- |
| Responsive Website        | ✅      | HTML/CSS/Bootstrap      |
| User Registration         | ✅      | Django                  |
| User Login                | ✅      | Django Auth             |
| User Logout               | ✅      | Django Auth             |
| Protected Page            | ✅      | Django                  |
| AI Assistant              | ✅      | Django + WorqHat        |
| Nutrition Finder          | ✅      | Django + API Ninjas     |
| Exercise Section          | ✅      | Django Templates        |
| Meditation Section        | ✅      | Django Templates        |
| Mindfulness Section       | ✅      | Django Templates        |
| Sleep Section             | ✅      | Django Templates        |
| Mental Health Section     | ✅      | Django Templates        |
| Health Categories         | ✅      | Django Templates        |
| Articles & Resources      | ✅      | Django Templates        |
| Daily Planner             | 🟡     | Frontend/feature module |
| Hydration Reminders       | 🟡     | Frontend/feature module |
| Smart Health Tracking     | 🟡     | Feature concept         |
| Production Deployment     | 🔵     | Future enhancement      |
| Advanced Health Analytics | 🔵     | Future enhancement      |

### Status Legend

* ✅ Implemented
* 🟡 Partially implemented / feature module
* 🔵 Planned / future enhancement

---

# 🧪 Testing

Before deployment, the following areas should be tested:

### Authentication

* [ ] Register a new user.
* [ ] Attempt duplicate username registration.
* [ ] Attempt duplicate email registration.
* [ ] Test invalid login credentials.
* [ ] Test successful login.
* [ ] Test logout.
* [ ] Test access to protected pages without authentication.

### AI Assistant

* [ ] Send a valid prompt.
* [ ] Send an empty prompt.
* [ ] Send invalid JSON.
* [ ] Test missing API key.
* [ ] Test API timeout/error handling.
* [ ] Verify AI response is displayed correctly.

### Nutrition Finder

* [ ] Search for a valid food.
* [ ] Search for an unknown food.
* [ ] Test empty input.
* [ ] Test API failure.
* [ ] Verify returned nutrition data.

---

# 🚀 Deployment Considerations

Before deploying HealthSphere to production, the following improvements should be made.

## Django Configuration

Change:

```python
DEBUG = True
```

to:

```python
DEBUG = False
```

Configure:

```python
ALLOWED_HOSTS = [...]
```

Use a secure production secret key.

---

## Database

The development configuration currently uses SQLite.

For production, consider:

```text
PostgreSQL
```

or another production-grade relational database.

---

## API Security

API keys should be stored using:

* Environment variables
* Secret managers
* Deployment platform secrets

Never place them directly in Python source code.

---

## HTTPS

Production deployment should use HTTPS to protect:

* User credentials
* Sessions
* API requests
* Personal information

---

# 🔮 Future Enhancements

HealthSphere can be expanded significantly in future versions.

## 👤 Personalized Health Profiles

Create a profile containing:

* Age
* Height
* Weight
* Fitness goals
* Dietary preferences
* Activity level
* Sleep goals

---

## 📈 Health Dashboard

Create a centralized dashboard displaying:

* Calories
* Water intake
* Exercise
* Sleep
* Mood
* Weight
* Fitness progress

---

## 📊 Data Visualization

Add charts for:

* Weekly calorie intake
* Exercise progress
* Sleep duration
* Hydration
* Weight changes
* Mood trends

---

## 🤖 Advanced AI Personalization

The AI assistant could use user-provided information to generate more personalized:

* Workout plans
* Meal suggestions
* Sleep recommendations
* Stress-management suggestions
* Wellness routines

---

## 🗃️ Persistent Health Data

Create Django models for storing:

```text
User
 │
 ├── Health Profile
 ├── Exercise Records
 ├── Nutrition Records
 ├── Sleep Records
 ├── Hydration Records
 ├── Mood Records
 └── AI Conversations
```

---

## 🔔 Notifications

Add reminders for:

* Drinking water
* Exercise
* Meals
* Meditation
* Sleep
* Daily goals

---

## 📱 Mobile Application

A future version could provide:

* Android application
* iOS application
* Push notifications
* Mobile health dashboard

---

# ⚠️ Current Project Limitations

HealthSphere is currently a development/academic project rather than a production medical platform.

Some features are implemented as frontend modules or concepts and are not yet connected to a complete persistent health-data system.

The repository also contains several educational, template-derived, and experimental modules. Therefore, the project structure contains multiple Django projects rather than one completely consolidated production architecture.

The main Django application's `models.py` currently does not define custom HealthSphere database models, so advanced persistent health tracking is a natural area for future development.

---

# 🛡️ Medical Disclaimer

HealthSphere is intended for:

* Educational purposes
* General wellness support
* Health information
* Software-development demonstration

It is **not a replacement for professional medical advice, diagnosis, or treatment**.

AI-generated information may be inaccurate or incomplete.

Users should consult qualified healthcare professionals for medical decisions.

---

# 📚 Credits

The repository includes frontend/template assets derived from the:

**Kider - Preschool Website Template**

by:

**HTML Codex**

The original template information is documented in:

```text
READ-ME.txt
LICENSE.txt
```

The repository's `READ-ME.txt` identifies the original template, author, template license, and HTML Codex website.

---

# 🔗 External Technologies

HealthSphere uses or references the following technologies:

* [Django](https://www.djangoproject.com/)
* [Python](https://www.python.org/)
* [Bootstrap](https://getbootstrap.com/)
* [JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
* [WorqHat AI](https://worqhat.com/)
* [API Ninjas](https://api-ninjas.com/)
* [Font Awesome](https://fontawesome.com/)
* [Owl Carousel](https://owlcarousel2.github.io/OwlCarousel2/)
* [HTML Codex](https://htmlcodex.com/)

---

# 📜 License

See:

```text
LICENSE.txt
```

for the license information included with the repository.

Template-derived assets should be used according to their original license terms.

---

# 👨‍💻 Author

## Pranish Belsare

Computer Science / AI & ML Student

GitHub:

**[@ThePranish03](https://github.com/ThePranish03)**

---

# ⭐ Project Vision

HealthSphere aims to evolve into a unified digital wellness platform where users can:

```text
                    HEALTHSPHERE
                         │
        ┌────────────────┼────────────────┐
        │                │                │
        ▼                ▼                ▼
    Physical          Nutrition        Mental
     Health             │              Wellness
        │               │                │
        └───────────────┼────────────────┘
                        │
                        ▼
                 AI Health Assistant
                        │
                        ▼
                Personalized Guidance
                        │
                        ▼
                  Healthy Lifestyle
```

The long-term vision is to combine **AI, health tracking, nutrition, fitness, mindfulness, and personalized wellness planning** into one accessible platform.

---

<p align="center">
  <strong>HealthSphere — Your digital companion for a healthier lifestyle. 🩺💙</strong>
</p>
