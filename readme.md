# Project Name

A web application built with Laravel, Vue.js, PostgreSQL, Nginx, and Docker.

## Tech Stack

- **Backend**: Laravel
- **Frontend**: Vue.js
- **Database**: PostgreSQL
- **Web Server**: Nginx
- **Containerization**: Docker

## Prerequisites

- Docker
- Docker Compose

## Getting Started

1. Clone the repository:
```bash
git clone <repository-url>
```

2. Run the application:
```bash
docker-compose up -d --build
```

3. Run database migrations:
```bash
docker-compose exec app php artisan migrate
```

## API Documentation
## Authentication Routes

### Register
 - Endpoint: POST /api/register
 - Route Name: register

 Request Body
 ```json
 {
    "name": "test",
    "email": "test@gmail.com",
    "password": "secret123",
    "password_confirmation": "secret123"
 }
 ```

 Response (201 Created)
 ```json
 {
    "name": "test",
    "email": "test@gmail.com",
    "updated_at": "2025-03-13T14:02:34.000000Z",
    "created_at": "2025-03-13T14:02:34.000000Z",
    "id": 1
 }
 ```

### Register
 - Endpoint: POST /api/login
 - Route Name: login

 Request Body
 ```json
 {
    "email": "test@gmail.com",
    "password": "secret123"
 }
 ```

 Response (200 OK)
 ```json
 {
    "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbG9jYWxob3N0OjgwODAvYXBpL2F1dGgvbG9naW4iLCJpYXQiOjE3NDE4NzQ2OTAsImV4cCI6MTc0MTg3ODI5MCwibmJmIjoxNzQxODc0NjkwLCJqdGkiOiJtdm8walJoSmlqTXhJalBQIiwic3ViIjoiMSIsInBydiI6IjIzYmQ1Yzg5NDlmNjAwYWRiMzllNzAxYzQwMDg3MmRiN2E1OTc2ZjcifQ.icUgnuDNJhFTT0VXa7aejiCtPRM5o49TdbNHKNuxji4",
    "token_type": "bearer",
    "expires_in": 3600
 }
 ```
## Additional Auth Routes
- POST /api/logout - Logout (requires authentication)
- POST /api/refresh - Refresh token (requires authentication)
- POST /api/me - Get authenticated user details (requires authentication)

## Frontend
The frontend is a standalone Vue.js application running on http://localhost:5173

## Pages
Register
- URL: /register

Login
- URL: /login

Dashboard
- URL: /dashboard