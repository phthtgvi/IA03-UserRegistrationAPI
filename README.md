# IA03 - User Registration API with React Frontend

A complete User Registration System built with NestJS backend and React frontend.

## Tech Stack

### Backend

- NestJS
- TypeORM
- PostgreSQL
- bcrypt (password hashing)
- class-validator (validation)

### Frontend

- React 18
- Vite
- TypeScript
- Tailwind CSS
- React Hook Form
- React Query (@tanstack/react-query)
- React Router DOM

## Features

- User registration with email and password
- Password hashing using bcrypt
- Email validation and duplicate checking
- Form validation with React Hook Form
- API state management with React Query
- Responsive UI with Tailwind CSS
- Error handling and user feedback
- CORS enabled for frontend-backend communication

## Prerequisites

Before running this project, make sure you have:

- Node.js (v18 or higher)
- PostgreSQL installed and running
- npm or yarn package manager

## Installation

### 1. Clone the repository

```bash
git clone <repository-url>
cd IA03-UserRegistrationAPI
```

### 2. Setup Backend

```bash
cd server
npm install
```

Create a `.env` file in the server directory:

```env
DATABASE_HOST=localhost
DATABASE_PORT=5432
DATABASE_USER=postgres
DATABASE_PASSWORD=your_password
DATABASE_NAME=user_registration
PORT=3000
```

Create PostgreSQL database:

```bash
psql -U postgres
CREATE DATABASE user_registration;
\q
```

### 3. Setup Frontend

```bash
cd ../client
npm install
```

Create a `.env` file in the client directory (optional):

```env
NEXT_PUBLIC_API_URL=http://localhost:3000
```

## Running the Application

### Start Backend Server

```bash
cd server
npm run start:dev
```

The backend will run on `http://localhost:3000`

### Start Frontend Application

Open a new terminal:

```bash
cd client
npm run dev
```

The frontend will run on `http://localhost:5173`

## API Endpoints

### POST /user/register

Register a new user.

**Request Body:**

```json
{
  "email": "user@example.com",
  "password": "password123"
}
```

**Success Response (201):**

```json
{
  "message": "User registered successfully",
  "user": {
    "email": "user@example.com",
    "createdAt": "2024-01-01T00:00:00.000Z"
  }
}
```

**Error Responses:**

- 409: Email already exists
- 400: Validation error
- 500: Internal server error

## Project Structure

```
IA03-UserRegistrationAPI/
├── server/
│   ├── src/
│   │   ├── user/
│   │   │   ├── dto/
│   │   │   │   └── register.dto.ts
│   │   │   ├── user.controller.ts
│   │   │   ├── user.service.ts
│   │   │   ├── user.entity.ts
│   │   │   └── user.module.ts
│   │   ├── app.module.ts
│   │   └── main.ts
│   ├── package.json
│   └── tsconfig.json
│
└── client/
    ├── src/
    │   ├── api/
    │   │   └── auth.ts
    │   ├── pages/
    │   │   ├── Home.tsx
    │   │   ├── Login.tsx
    │   │   └── SignUp.tsx
    │   ├── App.tsx
    │   ├── main.tsx
    │   └── index.css
    ├── package.json
    └── vite.config.ts
```

## Usage

1. Open your browser and navigate to `http://localhost:5173`
2. Click "Get Started - Sign Up" on the home page
3. Fill in the registration form with a valid email and password (minimum 6 characters)
4. Submit the form to create a new account
5. You can also test the Login page (UI only, no backend authentication implemented)

## Development

### Backend Development

```bash
cd server
npm run start:dev  # Watch mode
npm run build      # Production build
npm run lint       # Run linter
```

### Frontend Development

```bash
cd client
npm run dev        # Development server
npm run build      # Production build
npm run preview    # Preview production build
```

## Validation Rules

### Email

- Required field
- Must be a valid email format
- Must be unique (no duplicates)

### Password

- Required field
- Minimum 6 characters
- Hashed before storage using bcrypt

## Security Features

- Passwords are hashed using bcrypt with 10 salt rounds
- Environment variables for sensitive configuration
- CORS enabled with specific origins
- Input validation on both frontend and backend
- Global validation pipe in NestJS

## Error Handling

The application provides clear error messages for:

- Invalid email format
- Password too short
- Email already registered
- Network errors
- Server errors

## Future Enhancements

- User authentication (login functionality)
- JWT token-based authentication
- Password reset functionality
- Email verification
- User profile management
- Session management

## License

MIT
