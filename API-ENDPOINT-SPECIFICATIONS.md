# API Endpoint Specifications

## Authentication

### 1. Login
- **Endpoint:** `/api/auth/login`
- **Method:** `POST`
- **Request Headers:**
  - `Content-Type: application/json`

- **Request Body:**
  ```json
  {
    "username": "string",
    "password": "string"
  }
  ```

- **Response:**
  - **Status Code:** 200 OK
  - **Response Body:**
    ```json
    {
      "token": "string",
      "expiresIn": 3600
    }
    ```
  - **Error Handling:**
    - **401 Unauthorized:** Invalid username or password.

### 2. Logout
- **Endpoint:** `/api/auth/logout`
- **Method:** `POST`
- **Request Headers:**
  - `Authorization: Bearer {token}`

- **Response:**
  - **Status Code:** 204 No Content

## User Management

### 1. Create User
- **Endpoint:** `/api/users`
- **Method:** `POST`
- **Request Headers:**
  - `Content-Type: application/json`
  - `Authorization: Bearer {token}`

- **Request Body:**
  ```json
  {
    "username": "string",
    "password": "string",
    "email": "string"
  }
  ```

- **Response:**
  - **Status Code:** 201 Created
  - **Response Body:**
    ```json
    {
      "id": "string",
      "username": "string",
      "email": "string"
    }
    ```
  - **Error Handling:**
    - **400 Bad Request:** Missing or invalid data.

### 2. Get User by ID
- **Endpoint:** `/api/users/{id}`
- **Method:** `GET`
- **Request Headers:**
  - `Authorization: Bearer {token}`

- **Response:**
  - **Status Code:** 200 OK
  - **Response Body:**
    ```json
    {
      "id": "string",
      "username": "string",
      "email": "string"
    }
    ```
  - **Error Handling:**
    - **404 Not Found:** User with ID not found.

## Role Assignment

### 1. Assign Role to User
- **Endpoint:** `/api/users/{id}/roles`
- **Method:** `POST`
- **Request Headers:**
  - `Content-Type: application/json`
  - `Authorization: Bearer {token}`

- **Request Body:**
  ```json
  {
    "role": "string"
  }
  ```

- **Response:**
  - **Status Code:** 204 No Content
  - **Error Handling:**
    - **404 Not Found:** User with ID not found.

## Permission Endpoints

### 1. Get Permissions
- **Endpoint:** `/api/permissions`
- **Method:** `GET`
- **Request Headers:**
  - `Authorization: Bearer {token}`

- **Response:**
  - **Status Code:** 200 OK
  - **Response Body:**
    ```json
    [
      {
        "id": "string",
        "name": "string"
      }
    ]
    ```
