# Todo REST API (Django REST Framework)

Professional Todo API with JWT authentication, per-user data isolation, filtering, search, and pagination.

## Features

- JWT authentication (`/api/auth/token/`, `/api/auth/token/refresh/`)
- User registration endpoint (`/api/auth/register/`)
- Todo CRUD with ownership enforcement
- Filtering by completion status (`?is_completed=true`)
- Search by title (`?search=keyword`)
- Global pagination enabled (page size: 10)

## Project Structure

```
.
├── config/
│   ├── settings.py
│   ├── urls.py
│   ├── asgi.py
│   └── wsgi.py
├── apps/
│   ├── users/
│   │   ├── serializers.py
│   │   ├── views.py
│   │   └── urls.py
│   └── todos/
│       ├── models.py
│       ├── serializers.py
│       ├── permissions.py
│       ├── views.py
│       ├── urls.py
│       └── migrations/
├── manage.py
└── requirements.txt
```

## Setup

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver
```

## API Endpoints

- `POST /api/auth/register/` - Register a user
- `POST /api/auth/token/` - Obtain JWT access/refresh tokens
- `POST /api/auth/token/refresh/` - Refresh access token
- `GET|POST /api/todos/` - List/Create todos (current user only)
- `GET|PUT|PATCH|DELETE /api/todos/{id}/` - Retrieve/Update/Delete own todo

## Example Query Params

- `/api/todos/?is_completed=true`
- `/api/todos/?search=meeting`
- `/api/todos/?page=2`
