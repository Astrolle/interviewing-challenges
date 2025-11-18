# Full-Stack Take-Home Assignment

## Project: Simple Task Management Application

Build a task management application where users can create, view, update, and delete their tasks.

---

## Core Requirements

### Backend (NestJS)

**Required Features:**

1. **Authentication System**
   - User registration (email, password, name)
   - User login (JWT-based)
   - Protected routes

2. **Task Management API**
   - Create a task (title, description, status, priority, dueDate)
   - Get all tasks for logged-in user
   - Get single task by ID
   - Update task
   - Delete task
   - Filter tasks by status (pending, in-progress, completed)

3. **Technical Requirements**
   - Use **Mongoose with MongoDB**
   - Proper DTOs with validation (class-validator)
   - JWT authentication
   - Proper error handling
   - Password hashing (bcrypt)
   - Environment variables for config

**API Endpoints Expected:**

```js
POST   "/auth/register"
POST   "/auth/login"
GET    "/auth/profile"

GET    "/tasks"
POST   "/tasks"
GET    "/tasks/:id"
PATCH  "/tasks/:id"
DELETE "/tasks/:id"
GET    "/tasks?status=completed"
```

---

### Frontend (React)

**Required Features:**

1. **Authentication Pages**
   - Login page
   - Registration page
   - Protected routes (redirect to login if not authenticated)
   - Logout functionality

2. **Task Management UI**
   - Dashboard showing all tasks
   - Create new task form
   - Edit task (inline or modal)
   - Delete task with confirmation
   - Mark task as complete
   - Filter tasks by status
   - Display task priority with visual indicators

3. **Technical Requirements**
   - Use React 18+ with hooks
   - Form validation
   - Loading states
   - Error handling and display
   - Responsive design (mobile-friendly)
   - Clean component structure
   - Usage of Zustand or any other state manager

---

### What are we looking for in general

- ✅ Git commit history (meaningful commits)
- ✅ Clean, readable code
- ✅ Proper TypeScript usage

---

## MongoDB Schema Design

### User Schema (Mongoose)

```typescript
{
  email: { type: String, required: true, unique: true },
  password: { type: String, required: true }, // hashed
  name: { type: String, required: true },
  createdAt: { type: Date, default: Date.now },
  updatedAt: { type: Date, default: Date.now }
}
```

### Task Schema (Mongoose)

```typescript
{
  title: { type: String, required: true },
  description: { type: String },
  status: { 
    type: String, 
    enum: ['pending', 'in-progress', 'completed'],
    default: 'pending' 
  },
  priority: { 
    type: String, 
    enum: ['low', 'medium', 'high'],
    default: 'medium' 
  },
  dueDate: { type: Date },
  userId: { type: Schema.Types.ObjectId, ref: 'User', required: true },
  createdAt: { type: Date, default: Date.now },
  updatedAt: { type: Date, default: Date.now }
}
```

## Tech Stack

- Backend: NestJS, MongoDB, Mongoose, JWT
- Frontend: React, TypeScript

## API Documentation

### Authentication

- POST /auth/register - Register new user
- POST /auth/login - Login user
- GET /auth/profile - Get user profile (Protected)

### Tasks

- GET /tasks - Get all tasks (Protected)
- POST /tasks - Create task (Protected)
- GET /tasks/:id - Get task by ID (Protected)
- PATCH /tasks/:id - Update task (Protected)
- DELETE /tasks/:id - Delete task (Protected)
- GET /tasks?status=completed - Filter tasks (Protected)

## Questions Candidates Can Ask

Candidates should feel free to:

- Choose their preferred React styling solution (CSS Modules, Styled Components, Tailwind, Material-UI)
- Use Context API or Zustand or any other
- Make reasonable assumptions about UI/UX (document them)
- Ask clarifying questions
- Focus on functionality over pixel-perfect design

---
