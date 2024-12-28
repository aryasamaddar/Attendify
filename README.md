# Attendify

Attendify is a modern attendance management application that uses OTP-based verification and optional location tracking for enhanced security and accuracy.

---

## Features

### Core Features

- **Smart Attendance Tracking**

  - OTP-based verification system

- **Location Services**

  - Distance calculation from class location

- **User Management**
  - Role-based access control (Admin, Teacher, Student)
  - Customizable user profiles

### Additional Features

- **Analytics & Reporting**

  - Attendance statistics and trends
  - Exportable reports (PDF, CSV)
  - Custom date range analysis
  - Individual & group attendance patterns

- **Security Features**
  - oAuth2
  - jwt

---

## Tech Stack

- **Backend**: Node.js, Express.js, Prisma
- **Frontend**: React.js
- **Database**: PostgreSQL
- **Other**: Axios, shadcn

---

## Installation

### Prerequisites

- Node.js (v14 or higher)
- PostgreSQL
- npm or yarn

### Steps

1. Clone the repository

```bash
git clone https://github.com/dasakash26/attendify.git
cd attendify
```

2. Install dependencies

```bash
npm install
```

3. Set up environment variables

```bash
cp .env.example .env
```

Edit `.env` with your database and other configuration details.

4. Run database migrations

```bash
npx prisma migrate dev
```

5. Start the development server

```bash
npm run dev
```

---

## API Endpoints

### **Auth**

- **POST /api/auth/register**: Register a new user.

  - Request Body: `{ "username": "string", "password": "string", "email": "string" }`
  - Response: `{ "message": "User registered successfully", "user": { ... } }`

- **POST /api/auth/login**: Login user and generate a token.
  - Request Body: `{ "username": "string", "password": "string" }`
  - Response: `{ "token": "jwt_token", "user": { ... } }`

### **Attendance**

- **POST /api/attendance/mark**: Mark attendance with OTP and optional geolocation.

  - Request Body: `{ "otp": "string", "location": { "lat": "number", "lng": "number" } }`
  - Response: `{ "message": "Attendance marked successfully", "attendance": { ... } }`

- **GET /api/attendance/:id**: Fetch attendance records for a user.
  - Path Parameter: `id` (User ID)
  - Response: `{ "attendanceRecords": [ ... ] }`

### **Users**

- **GET /api/users/profile**: Get current user's profile.

  - Response: `{ "user": { ... } }`

- **PUT /api/users/profile**: Update user profile.

  - Request Body: `{ "username": "string", "email": "string", "otherFields": "..." }`
  - Response: `{ "message": "Profile updated successfully", "user": { ... } }`

- **GET /api/users/:id**: Get user by ID (admin only).
  - Path Parameter: `id` (User ID)
  - Response: `{ "user": { ... } }`

### **Classes**

- **POST /api/classes**: Create a new class.

  - Request Body: `{ "name": "string", "description": "string", "otherFields": "..." }`
  - Response: `{ "message": "Class created successfully", "class": { ... } }`

- **GET /api/classes**: List all classes.

  - Response: `{ "classes": [ ... ] }`

- **PUT /api/classes/:id**: Update class details.

  - Path Parameter: `id` (Class ID)
  - Request Body: `{ "name": "string", "description": "string", "otherFields": "..." }`
  - Response: `{ "message": "Class updated successfully", "class": { ... } }`

- **DELETE /api/classes/:id**: Delete a class.
  - Path Parameter: `id` (Class ID)
  - Response: `{ "message": "Class deleted successfully" }`

---

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## License

This project is not licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
