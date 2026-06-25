# Mergington High School Activities API

A super simple FastAPI application that allows students to view and sign up for extracurricular activities.

## Features

- View all available extracurricular activities
- Register/login with JWT authentication
- View current authenticated user profile
- Sign up for activities (authenticated)

## Getting Started

1. Install the dependencies:

   ```
   pip install -r ../requirements.txt
   ```

2. Run the application:

   ```
   python app.py
   ```

3. Open your browser and go to:
   - API documentation: http://localhost:8000/docs
   - Alternative documentation: http://localhost:8000/redoc

## API Endpoints

| Method | Endpoint                                                          | Description                                                         |
| ------ | ----------------------------------------------------------------- | ------------------------------------------------------------------- |
| GET    | `/activities`                                                     | Get all activities with their details and current participant count |
| POST   | `/auth/register`                                                  | Register a new user account                                         |
| POST   | `/auth/login`                                                     | Login and receive JWT token                                         |
| GET    | `/auth/me`                                                        | Get profile for current authenticated user                          |
| POST   | `/activities/{activity_name}/signup?email=student@mergington.edu` | Sign up for an activity (requires JWT)                             |
| DELETE | `/activities/{activity_name}/unregister?email=student@mergington.edu` | Unregister from an activity (requires JWT)                     |

### Authentication

For protected routes, include a bearer token in the `Authorization` header:

```
Authorization: Bearer <access_token>
```

## Data Model

The application uses a simple data model with meaningful identifiers:

1. **Activities** - Uses activity name as identifier:

   - Description
   - Schedule
   - Maximum number of participants allowed
   - List of student emails who are signed up

2. **Students** - Uses email as identifier:
   - Name
   - Grade level

All data is stored in memory, which means data will be reset when the server restarts.
