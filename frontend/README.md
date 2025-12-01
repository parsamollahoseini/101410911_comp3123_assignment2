# COMP3123 Assignment 2 - Frontend (React Application)

**Student Name:** Parsa Mollahoseini  
**Student ID:** 101410911

## 📱 Frontend Overview

React-based employee management dashboard with Material-UI design, featuring user authentication, employee CRUD operations, file uploads, and search functionality.

## 🚀 Technology Stack

- **React** 18.x
- **Material-UI (MUI)** - Professional UI components
- **TanStack Query** (React Query) - Server state management
- **Axios** - HTTP client
- **React Router DOM** - Client-side routing
- **React Context API** - Global authentication state

## 📁 Project Structure
```
frontend/
├── public/
│   ├── index.html
│   └── favicon.ico
│
├── src/
│   ├── pages/
│   │   ├── Login.jsx           # Login page
│   │   ├── Signup.jsx          # User registration
│   │   └── Dashboard.jsx       # Main employee list
│   │
│   ├── components/
│   │   ├── PrivateRoute.jsx    # Protected route wrapper
│   │   ├── EmployeeForm.jsx    # Add/Edit employee modal
│   │   └── EmployeeDetails.jsx # View employee modal
│   │
│   ├── services/
│   │   ├── api.js              # Axios instance with interceptors
│   │   └── authService.js      # API service functions
│   │
│   ├── context/
│   │   └── AuthContext.jsx     # Authentication context
│   │
│   ├── App.js                  # Main app with routing
│   └── index.js                # Entry point
│
├── Dockerfile                  # Docker container config
├── .dockerignore              # Docker ignore rules
├── package.json
└── .env                       # Environment variables
```

## ✨ Features

### Authentication
- ✅ User signup with validation
- ✅ User login with JWT tokens
- ✅ Logout functionality
- ✅ Protected routes
- ✅ Persistent login (localStorage)

### Employee Management
- ✅ List all employees in a table
- ✅ Add new employee with profile picture upload
- ✅ View employee details in modal
- ✅ Update employee information
- ✅ Delete employee with confirmation
- ✅ Search by department and position
- ✅ Avatar display for profile pictures

### UI/UX Features
- ✅ Material-UI design system
- ✅ Responsive layout
- ✅ Loading states with spinners
- ✅ Error handling with alerts
- ✅ Form validation
- ✅ Professional table design
- ✅ Modal dialogs
- ✅ File upload preview

## 🔧 Installation & Setup

### Prerequisites
- Node.js 18+
- npm or yarn

### Install Dependencies
```bash
npm install --legacy-peer-deps
```

### Environment Variables

Create a `.env` file:
```env
REACT_APP_API_URL=http://localhost:4000/api/v1
```

For Docker deployment:
```env
REACT_APP_API_URL=http://localhost:4000/api/v1
```

### Run Development Server
```bash
npm start
```

Application runs at: `http://localhost:3000`

### Build for Production
```bash
npm run build
```

## 🐳 Docker Deployment

### Build Docker Image
```bash
docker build -t employee-frontend .
```

### Run Container
```bash
docker run -p 3000:3000 employee-frontend
```

### With Docker Compose (Recommended)

See parent directory's `docker-compose.yml`

## 📡 API Integration

### Axios Configuration

The app uses an Axios instance with:
- Base URL from environment variables
- Request interceptor to add JWT tokens
- Response interceptor for 401 error handling

### API Endpoints Used

#### Authentication
- `POST /user/signup` - Register new user
- `POST /user/login` - Login user

#### Employees
- `GET /emp/employees` - Get all employees
- `GET /emp/employees/:id` - Get employee by ID
- `POST /emp/employees` - Create employee (FormData with file)
- `PUT /emp/employees/:id` - Update employee (FormData with file)
- `DELETE /emp/employees?eid=:id` - Delete employee
- `GET /emp/employees/search?department=X&position=Y` - Search

## 🎨 UI Components

### Pages

**Login.jsx**
- Email and password fields
- Form validation
- Error messages
- Link to signup

**Signup.jsx**
- Username, email, password fields
- Password confirmation
- Client-side validation
- Success redirect

**Dashboard.jsx**
- AppBar with logout
- Search filters (department, position)
- Employee table with actions
- Add Employee button
- View/Edit/Delete modals

### Components

**EmployeeForm.jsx**
- Create/Update employee
- File upload with preview
- Form validation
- Material-UI Grid layout

**EmployeeDetails.jsx**
- Read-only employee view
- Avatar display
- Formatted data display

**PrivateRoute.jsx**
- Route protection
- Authentication check
- Redirect to login

## 🔐 Authentication Flow

1. User logs in → JWT token received
2. Token stored in localStorage
3. Token added to all API requests (Authorization header)
4. Protected routes check authentication
5. 401 errors → Redirect to login

## 📦 Key Dependencies
```json
{
  "react": "^18.3.1",
  "react-router-dom": "^6.28.0",
  "@mui/material": "^6.1.9",
  "@mui/icons-material": "^6.1.9",
  "@tanstack/react-query": "^5.62.7",
  "axios": "^1.7.9",
  "@emotion/react": "^11.14.0",
  "@emotion/styled": "^11.14.0"
}
```

## 🎯 Design Decisions

### Why Material-UI?
- Professional, consistent design system
- Responsive components out of the box
- Accessibility built-in
- Google Material Design standards

### Why TanStack Query?
- Automatic caching and refetching
- Loading and error states
- Cache invalidation
- Optimistic updates

### Why Context API?
- Simple global authentication state
- Avoid prop drilling
- Built-in React solution

## 🧪 Testing the App

1. **Signup Flow:**
    - Go to http://localhost:3000
    - Click "Sign Up"
    - Fill form and submit
    - Redirected to login

2. **Login Flow:**
    - Enter credentials
    - Should see dashboard

3. **Add Employee:**
    - Click "Add Employee"
    - Fill form, upload image
    - Submit and verify in table

4. **Search:**
    - Use department/position filters
    - Verify filtered results

5. **Edit/Delete:**
    - Click actions on any employee
    - Verify updates/deletions

## 🐛 Troubleshooting

### CORS Errors
- Ensure backend is running on port 4000
- Check REACT_APP_API_URL in .env

### Authentication Issues
- Clear localStorage
- Check JWT token validity
- Verify backend is running

### File Upload Not Working
- Check backend upload middleware
- Verify multipart/form-data content type
- Check file size limits

## 📝 Code Quality

- ✅ Modular component structure
- ✅ Separation of concerns (services, components, pages)
- ✅ Reusable components
- ✅ Error handling
- ✅ Loading states
- ✅ Clean code practices

## 🚀 Future Enhancements

- [ ] Unit tests with Jest
- [ ] E2E tests with Cypress
- [ ] Dark mode support
- [ ] Advanced filtering
- [ ] Pagination
- [ ] Employee export (CSV/PDF)
- [ ] Profile picture cropping

---

**Part of:** COMP3123 Assignment 2  
**Date:** November 2025  
**Backend Repository:** ../backend