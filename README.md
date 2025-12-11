# MediaBudgeter Backend - Django REST API

A Django REST Framework backend for MediaBudgeter application, providing CRUD operations for media items (movies, TV shows, etc.).

Live API
URL: https://backendfinalspeitel.onrender.com/api/

 Features
- User registration and authentication (Token-based)
- CRUD operations for media items
- Soft delete functionality
- Restore deleted items
- User-specific data isolation
- CORS support for React Native frontend
- Admin panel for data management

Tech Stack
- Django 5.2.7
- Django REST Framework
- SQLite/PostgreSQL
- Python 3.x
- Gunicorn
- WhiteNoise for static files

Installation & Setup

Local Development

1. Clone the repository:
   ```bash
   git clone https://github.com/AndreDizon/BackEndFinalsPEITEL.git
   cd backend
   ```

2. Create a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Run migrations:
   ```bash
   python manage.py migrate
   ```

5. Create a superuser:
   ```bash
   python manage.py createsuperuser
   ```

6. Start the server:
   ```bash
   python manage.py runserver 0.0.0.0:8000
   ```

API Endpoints

Authentication
- `POST /api/auth/register/` - Register new user
- `POST /api/auth/login/` - Login user
- `POST /api/auth/logout/` - Logout user

Media Items (CRUD)
- `GET /api/media-items/` - List all media items
- `POST /api/media-items/` - Create new media item
- `GET /api/media-items/{id}/` - Get media item details
- `PUT /api/media-items/{id}/` - Update media item
- `DELETE /api/media-items/{id}/` - Delete (soft delete) media item
- `GET /api/media-items/deleted/` - List deleted items
- `POST /api/media-items/{id}/restore/` - Restore deleted item
- `POST /api/media-items/{id}/unmark_finished/` - Change status back to watching

Database
Default: SQLite (db.sqlite3)
Production: PostgreSQL 

Example Request

Register a new user:
```bash
curl -X POST https://backendfinalspeitel.onrender.com/api/auth/register/ \
  -H "Content-Type: application/json" \
  -d '{"username":"testuser","password":"Pass123","password2":"Pass123"}'
```

Response:
```json
{
  "key": "token_string_here",
  "user": {
    "id": 1,
    "username": "testuser",
    "email": ""
  }
}
```

Deployment (Render.com)

1. Push to GitHub
2. Create New Web Service on Render.com
3. Connect BackEndFinalsPEITEL repository
4. Set build command: `pip install -r requirements.txt`
5. Set start command: `gunicorn config.wsgi:application`
6. Add environment variables (if needed)
7. Deploy

Team Members
- Andre Dizon
- Mark Angelo Dela Cruz
- Caryl Loise Dizon


Links
- Frontend Repository: https://github.com/AndreDizon/FrontEndFinalsPEITEL
- Frontend (Snack): https://snack.expo.dev/@angenoise/final-project
- Backend API: https://backendfinalspeitel.onrender.com/api/
- Backend Repository: https: https://github.com/AndreDizon/BackEndFinalsPEITEL.git
