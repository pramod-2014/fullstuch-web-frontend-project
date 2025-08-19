# Professional React Frontend

A modern, responsive React frontend application with authentication, user management, and API integration.

## Features

- **Authentication**: Complete login/signup flows with JWT token management
- **Protected Routes**: Route guards for authenticated users only
- **User Management**: Dashboard with user statistics and management table
- **Profile Management**: Edit user profile information
- **Professional UI**: Clean, modern design with shadcn/ui components
- **Responsive Design**: Works on all device sizes
- **API Integration**: Ready to connect to external REST APIs

## Tech Stack

- **React 18** with TypeScript
- **Vite** for fast development and building
- **React Router** for client-side routing
- **Axios** for API requests
- **TailwindCSS** for styling
- **shadcn/ui** for UI components
- **Context API** for state management

## Setup Instructions

### 1. Install Dependencies

```bash
npm install
```

### 2. Environment Configuration

Create a `.env` file in the root directory and configure your API base URL:

```bash
# Copy the example file
cp .env.example .env

# Edit .env and set your API URL
VITE_API_BASE_URL=https://your-api-domain.com
```

### 3. Start Development Server

```bash
npm run dev
```

The application will be available at `http://localhost:5173`

## API Contract

This frontend expects the following API endpoints:

### Authentication
- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User login

### Users
- `GET /api/users/me` - Get current user profile
- `GET /api/users` - Get all users (requires auth)
- `PUT /api/users/:id` - Update user (requires auth)
- `DELETE /api/users/:id` - Delete user (requires auth)

## Project Structure

```
src/
├── components/          # Reusable UI components
│   ├── ui/             # shadcn/ui components
│   ├── Layout.tsx      # Main layout wrapper
│   └── ProtectedRoute.tsx
├── context/            # React Context providers
│   └── AuthContext.tsx # Authentication state management
├── pages/              # Page components
│   ├── Login.tsx
│   ├── Signup.tsx
│   ├── Dashboard.tsx
│   ├── Profile.tsx
│   └── NotFound.tsx
├── services/           # API service layer
│   └── api.ts         # Axios configuration and API calls
├── types/             # TypeScript type definitions
│   └── auth.ts
└── hooks/             # Custom React hooks
```

## Key Features

### Authentication Flow
- JWT token stored in localStorage and memory
- Automatic token attachment to API requests
- Session restoration on app reload
- Protected route guards

### Dashboard
- User statistics cards
- Sortable users table
- User management actions (edit/delete)
- Responsive design

### Profile Management
- View current user information
- Edit username, email, and role
- Form validation with error handling
- Real-time updates

## Environment Variables

| Variable | Description | Required |
|----------|-------------|----------|
| `VITE_API_BASE_URL` | Base URL for your API | Yes |

## Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build
- `npm run lint` - Run ESLint

## Production Deployment

1. Set the correct `VITE_API_BASE_URL` in your environment
2. Build the application: `npm run build`
3. Deploy the `dist` folder to your hosting provider

## Browser Support

This application supports all modern browsers including:
- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)