# Backend Requirement Specifications

## Overview
This document outlines the **functional** and **technical requirements** for key backend features of the **Property Booking System**.  
The backend is designed as a **RESTful API** that supports scalability, security, and data consistency.

---

## 1. User Authentication

### Objective
Allow users to securely register, log in, and manage access to the system.

### Functional Requirements
- Users should be able to register using their email, password, and full name.
- The system must securely store user credentials using password hashing (e.g., bcrypt).
- Users must be able to log in using valid credentials.
- JWT (JSON Web Token) should be used for authentication and authorization.
- Password reset functionality should be available through email.

### API Endpoints

| Method | Endpoint              | Description                       |
| ------ | --------------------- | --------------------------------- |
| `POST` | `/api/register`       | Register a new user               |
| `POST` | `/api/login`          | Authenticate user and issue JWT   |
| `POST` | `/api/logout`         | Invalidate a user’s session token |
| `POST` | `/api/password/reset` | Reset a user’s password           |

### Input / Output Specification

#### Register Response
```json
{
  "message": "Registration successful",
  "user": {
    "id": 1,
    "name": "John Doe",
    "email": "john@example.com"
  },
  "token": "jwt_token_here"
}
```

# 1. Authentication System

## Login Request
```json
{
  "email": "john@example.com",
  "password": "SecurePassword123"
}
```

# Login Response
```json
{
  "message": "Login successful",
  "token": "jwt_token_here",
  "user": {
    "id": 1,
    "name": "John Doe",
    "email": "john@example.com"
  }
}
```

# System Specifications

## 1. User Authentication

### Objective
Provide secure user registration and login functionalities with JWT-based authentication.

### Functional Requirements
- Users must be able to register and log in using email and password.  
- JWT tokens should be used for session management.  
- Passwords must be hashed before storage.  
- Token expiration and refresh mechanisms must be implemented.

### API Endpoints
| Method | Endpoint      | Description                  |
| ------ | ------------- | ---------------------------- |
| POST   | /api/register | Register a new user          |
| POST   | /api/login    | Log in and generate a token  |
| GET    | /api/user     | Retrieve user profile (auth) |

### Input / Output Specification

#### Register Request
```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "SecurePassword123"
}
```