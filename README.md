# Django REST Framework Authentication and Permissions

This project demonstrates a complete implementation of JWT authentication and various permission levels in DRF.

## Features implemented
- **JWT Authentication**: Using `djangorestframework-simplejwt`.
- **User Registration**: Custom serializer and view for new user signups.
- **User Profile Management**: Retrieve and update profile details.
- **Password Management**: Change password endpoint.
- **Permission Classes**:
    - `AllowAny`: Public endpoints (Registration, Public Demo).
    - `IsAuthenticated`: Protected endpoints (Profile, Notes).
    - `IsAdminUser`: Admin-only demonstration.
- **Custom Permissions**:
    - `IsOwnerOrReadOnly`: Object-level permission for the `Note` model.
    - Role-based logical demonstration.

## Installation

1. Install dependencies:
   ```bash
   pip install django djangorestframework djangorestframework-simplejwt
   ```

2. Run migrations:
   ```bash
   python manage.py makemigrations
   python manage.py migrate
   ```

3. Create a superuser (optional, for admin access):
   ```bash
   python manage.py createsuperuser
   ```

4. Run the server:
   ```bash
   python manage.py runserver
   ```

## Testing with Postman

1. Import the `drf_auth_collection.json` file into Postman.
2. Set the `base_url` variable (default: `http://127.0.0.1:8000`).
3. Follow the sequence:
   - **Register User**: Create a new account.
   - **Login**: This will automatically save the `access_token` and `refresh_token` to Postman variables.
   - **Get Profile**: Verify you can access protected data.
   - **Create Note**: Test object-level permissions.

## Authentication Errors handled
- **401 Unauthorized**: Missing or invalid token.
- **403 Forbidden**: Insufficient permissions (e.g., non-admin accessing admin endpoint).
- **400 Bad Request**: Invalid credentials or validation errors.

## Project Structure
- `core/`: Project configuration and settings.
- `authentication_app/`: Main logic for users, notes, and permissions.
  - `serializers.py`: User and Note serializers.
  - `views.py`: API implementions.
  - `permissions.py`: Custom logic for access control.
  - `urls.py`: App-specific routing.

Please try visiting these specific API endpoints to see the DRF interface:

Public Demo: http://127.0.0.1:8000/api/auth/public/
Registration: http://127.0.0.1:8000/api/auth/register/
Login: http://127.0.0.1:8000/api/auth/login/
