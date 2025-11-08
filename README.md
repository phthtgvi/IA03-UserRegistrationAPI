# IA03 - User Registration API with React Frontend

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
