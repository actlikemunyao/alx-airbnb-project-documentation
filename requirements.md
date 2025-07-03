# Backend Requirements Specification

This document outlines the technical and functional requirements for the core features of the Airbnb backend system.

---

## 1. User Authentication

### Functional Requirements
- Users must be able to register, log in, and log out.
- Passwords should be securely hashed and stored.
- Users can reset their password.

### API Endpoints
- `POST /api/register` – Register a new user  
- `POST /api/login` – Authenticate user and return token  
- `POST /api/logout` – Invalidate session  
- `POST /api/password-reset` – Send password reset link  

### Input/Output Examples
- Input: `{ "email": "user@example.com", "password": "secret123" }`
- Output: `{ "token": "abc123", "user_id": 42 }`

### Validation Rules
- Email must be valid format and unique.
- Password must be at least 8 characters.

---

## 2. Property Management

### Functional Requirements
- Owners can list new properties and manage existing listings.
- Users can view property details.

### API Endpoints
- `POST /api/properties` – Create a new property  
- `GET /api/properties/:id` – Get property by ID  
- `PUT /api/properties/:id` – Update property  
- `DELETE /api/properties/:id` – Delete property  

### Input/Output
- Input: `{ "title": "Cozy Cabin", "price": 120.00, "location": "Nairobi" }`
- Output: `{ "property_id": 101, "status": "created" }`

### Validation
- Title must not be empty.
- Price must be a positive number.

---

## 3. Booking System

### Functional Requirements
- Users can book properties for specific dates.
- The system must prevent double-bookings.
- Booking must be tied to payments.

### API Endpoints
- `POST /api/bookings` – Create a new booking  
- `GET /api/bookings/:id` – Get booking info  
- `DELETE /api/bookings/:id` – Cancel booking  

### Input/Output
- Input: `{ "property_id": 101, "start_date": "2025-08-01", "end_date": "2025-08-05" }`
- Output: `{ "booking_id": 55, "status": "pending_payment" }`

### Validation
- Dates must be valid and in the future.
- No overlapping bookings allowed for the same property.

---

