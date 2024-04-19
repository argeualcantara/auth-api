# Authentication System API Documentation

Welcome to the documentation of the Authentication System API. This API provides endpoints for user authentication and management.

## Base URL

```
https://api.authsystem.com/v1
```

## Endpoints

### Register User

Endpoint to register a new user in the system.

- **URL:** `/register`
- **Method:** POST
- **Request body:**
  ```json
  {
    "username": "example_user",
    "email": "user@example.com",
    "password": "password123"
  }
  ```
- **Response example (success):**
  ```json
  {
    "id": 1,
    "username": "example_user",
    "email": "user@example.com",
    "message": "User registered successfully."
  }
  ```

### Login User

Endpoint to authenticate and login a user.

- **URL:** `/login`
- **Method:** POST
- **Request body:**
  ```json
  {
    "email": "user@example.com",
    "password": "password123"
  }
  ```
- **Response example (success):**
  ```json
  {
    "user_id": 1,
    "username": "example_user",
    "token": "<JWT_TOKEN>",
    "message": "Login successful."
  }
  ```

### Get User Profile

Endpoint to retrieve the profile of the authenticated user.

- **URL:** `/profile`
- **Method:** GET
- **Headers:**
  - `Authorization: Bearer <JWT_TOKEN>`
- **Response example (success):**
  ```json
  {
    "user_id": 1,
    "username": "example_user",
    "email": "user@example.com",
    "message": "User profile retrieved successfully."
  }
  ```

### Update User Profile

Endpoint to update the profile of the authenticated user.

- **URL:** `/profile`
- **Method:** PUT
- **Headers:**
  - `Authorization: Bearer <JWT_TOKEN>`
- **Request body:**
  ```json
  {
    "username": "new_username",
    "email": "new_email@example.com"
  }
  ```
- **Response example (success):**
  ```json
  {
    "user_id": 1,
    "username": "new_username",
    "email": "new_email@example.com",
    "message": "User profile updated successfully."
  }
  ```

### Logout User

Endpoint to logout the authenticated user and invalidate the JWT token.

- **URL:** `/logout`
- **Method:** POST
- **Headers:**
  - `Authorization: Bearer <JWT_TOKEN>`
- **Response example (success):**
  ```json
  {
    "message": "Logout successful."
  }
  ```

This is a basic outline of an authentication system API documentation. You can expand and customize it further according to your specific requirements.
