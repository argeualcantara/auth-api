# Authentication System API Integration Documentation

This documentation provides guidance on integrating the Authentication System API into your application for user authentication and management.

## API Base URL

The base URL for accessing the Authentication System API endpoints is:

```
https://api.authsystem.com/v1
```

## Authentication

The Authentication System API uses JWT (JSON Web Token) for authentication. After successful login, the API returns a JWT token that must be included in the headers of subsequent requests to authenticate the user.

### Obtaining JWT Token

To obtain a JWT token:

1. **Register a User:** Send a POST request to `/register` endpoint with user details (username, email, password) to register a new user.
2. **Login:** Send a POST request to `/login` endpoint with user's email and password to authenticate. The API will respond with a JWT token.

Example Request:
```http
POST /login HTTP/1.1
Host: api.authsystem.com
Content-Type: application/json

{
  "email": "user@example.com",
  "password": "password123"
}
```

Example Response:
```json
{
  "user_id": 1,
  "username": "example_user",
  "token": "<JWT_TOKEN>",
  "message": "Login successful."
}
```

### Using JWT Token

Include the JWT token in the `Authorization` header of subsequent requests as follows:

```http
Authorization: Bearer <JWT_TOKEN>
```

## API Endpoints

### 1. Register User

- **URL:** `/register`
- **Method:** POST
- **Request Body:** User details (username, email, password)
- **Response:** User ID, username, email, and success message.

### 2. Login User

- **URL:** `/login`
- **Method:** POST
- **Request Body:** User's email and password
- **Response:** User ID, username, JWT token, and success message.

### 3. Get User Profile

- **URL:** `/profile`
- **Method:** GET
- **Headers:** `Authorization: Bearer <JWT_TOKEN>`
- **Response:** User profile data (user ID, username, email).

### 4. Update User Profile

- **URL:** `/profile`
- **Method:** PUT
- **Headers:** `Authorization: Bearer <JWT_TOKEN>`
- **Request Body:** Updated user profile data (username, email)
- **Response:** Updated user profile data and success message.

### 5. Logout User

- **URL:** `/logout`
- **Method:** POST
- **Headers:** `Authorization: Bearer <JWT_TOKEN>`
- **Response:** Logout success message.

## Error Handling

The Authentication System API returns appropriate HTTP status codes along with error messages in case of errors. Handle these errors in your application accordingly.

## Example Integration

Below is an example of how to integrate the Authentication System API using JavaScript Fetch API:

```javascript
const apiUrl = 'https://api.authsystem.com/v1';
const loginEndpoint = `${apiUrl}/login`;

// Function to login user
async function loginUser(email, password) {
  const response = await fetch(loginEndpoint, {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json'
    },
    body: JSON.stringify({ email, password })
  });
  
  if (!response.ok) {
    throw new Error('Login failed');
  }
  
  const data = await response.json();
  return data.token;
}

// Example usage
loginUser('user@example.com', 'password123')
  .then(token => {
    console.log('JWT Token:', token);
    // Use token for authenticated requests
  })
  .catch(error => {
    console.error('Login failed:', error.message);
  });
```

## Conclusion

This documentation provides the necessary information to integrate the Authentication System API into your application. Follow the guidelines and examples provided to ensure successful integration and secure user authentication.
