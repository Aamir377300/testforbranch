# Task Management System 🚀

Hey there! Welcome to my full-stack task management application. I built this as part of a backend developer internship assignment, and I'm pretty excited to share it with you.

## What's This All About?

This is a production-ready task management system where users can create, manage, and track their tasks. It's got everything you'd expect from a modern web app - secure authentication, role-based access, and a clean, responsive interface.

The cool part? It's built with scalability in mind from day one. Whether you're handling 10 users or 10,000, the architecture is ready to grow with you.

## Tech Stack (The Good Stuff)

**Backend:**
- Node.js & Express - Because JavaScript everywhere is just easier
- MongoDB with Mongoose - NoSQL flexibility for the win
- JWT Authentication - Stateless and scalable
- Bcrypt - Keeping passwords safe and sound
- Swagger - Interactive API docs (developers will thank you)

**Frontend:**
- Next.js 14 - React with superpowers (SSR + CSR)
- TypeScript - Catching bugs before they happen
- Tailwind CSS - Beautiful UI without the CSS headaches
- Context API - Simple state management

## Quick Start (Get Running in 5 Minutes)

### What You'll Need
- Node.js (v16 or higher)
- MongoDB (local or MongoDB Atlas)
- A terminal and your favorite code editor

### Step 1: Clone and Setup Backend

```bash
# Navigate to backend
cd backend

# Install dependencies
npm install

# Setup environment variables
cp .env.example .env
```

Edit your `.env` file:
```env
NODE_ENV=development
PORT=5002
MONGODB_URI=mongodb://localhost:27017/task_management
JWT_SECRET=your_super_secret_key_here
JWT_EXPIRE=7d
```

```bash
# Start the backend
npm run dev
```

Backend runs on `http://localhost:5002` 🎉

### Step 2: Setup Frontend

```bash
# Navigate to frontend
cd frontend

# Install dependencies
npm install

# Setup environment
cp .env.local.example .env.local
```

Edit your `.env.local`:
```env
NEXT_PUBLIC_API_URL=http://localhost:5002/api/v1
```

```bash
# Start the frontend
npm run dev
```

Frontend runs on `http://localhost:3000` 🎨

### Step 3: Create an Admin User (Optional)

```bash
cd backend
npm run create-admin
```

This creates an admin account:
- Email: `admin@example.com`
- Password: `admin123`

## Features That'll Make You Smile

### For Regular Users
- ✅ Register and login securely
- ✅ Create tasks with titles, descriptions, and due dates
- ✅ Mark tasks as pending or completed
- ✅ Filter tasks by date (yesterday, today, tomorrow, or any date)
- ✅ Edit and delete your tasks
- ✅ Clean, intuitive dashboard

### For Admins
- ✅ Everything users can do, plus...
- ✅ View all registered users
- ✅ Check any user's profile and their tasks
- ✅ System-wide visibility

### Security Features (Because We Care)
- 🔒 Passwords hashed with bcrypt (10 salt rounds)
- 🔒 JWT tokens with expiration
- 🔒 Input validation on every request
- 🔒 Role-based access control
- 🔒 Protected API routes
- 🔒 CORS configured properly

## API Endpoints (The Developer's Playground)

### Authentication
```http
POST /api/v1/auth/register
POST /api/v1/auth/login
```

### Tasks (Protected Routes)
```http
GET    /api/v1/tasks           # Get all your tasks
GET    /api/v1/tasks/:id       # Get specific task
POST   /api/v1/tasks           # Create new task
PUT    /api/v1/tasks/:id       # Update task
DELETE /api/v1/tasks/:id       # Delete task
```

### Admin Routes
```http
GET /api/v1/users              # Get all users (admin only)
GET /api/v1/users/:id          # Get user profile (admin only)
GET /api/v1/users/:id/tasks    # Get user's tasks (admin only)
```

Want to try them out? Check the interactive docs at `http://localhost:5002/api-docs` 📚

## Testing the API

### Using Swagger UI (Easiest Way)
1. Start the backend
2. Go to `http://localhost:5002/api-docs`
3. Click "Authorize" and paste your JWT token
4. Try out any endpoint right in your browser!

### Using Postman or cURL

**Register a user:**
```bash
curl -X POST http://localhost:5002/api/v1/auth/register \
  -H "Content-Type: application/json" \
  -d '{
    "name": "John Doe",
    "email": "john@example.com",
    "password": "password123"
  }'
```

**Create a task:**
```bash
curl -X POST http://localhost:5002/api/v1/tasks \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_JWT_TOKEN" \
  -d '{
    "title": "Build something awesome",
    "description": "Make it scalable too!",
    "status": "pending"
  }'
```

## Project Structure (Where Everything Lives)

```
task-management-system/
├── backend/
│   ├── src/
│   │   ├── config/          # Database and Swagger setup
│   │   ├── controllers/     # Business logic lives here
│   │   ├── middleware/      # Auth, validation, error handling
│   │   ├── models/          # MongoDB schemas
│   │   ├── routes/          # API route definitions
│   │   ├── scripts/         # Utility scripts (like create-admin)
│   │   ├── utils/           # Helper functions
│   │   ├── app.js           # Express app configuration
│   │   └── server.js        # Server entry point
│   └── package.json
│
└── frontend/
    ├── app/                 # Next.js pages (App Router)
    │   ├── admin/          # Admin dashboard
    │   ├── dashboard/      # User dashboard
    │   ├── login/          # Login page
    │   └── register/       # Registration page
    ├── components/          # Reusable React components
    ├── context/            # Global state management
    ├── lib/                # API utilities
    ├── types/              # TypeScript type definitions
    └── package.json
```

## Scalability & Load Balancing (The Fun Part!)

Okay, so you've got users flooding in. Great problem to have! Here's how this system can scale from 100 to 100,000 users.

### Current Architecture (What We Have Now)

Right now, we're running a monolithic architecture with JWT authentication. This is already pretty scalable because:

1. **Stateless Authentication**: JWT tokens mean no session storage. Each request is independent, so you can add more servers without worrying about session synchronization.

2. **Database Indexing**: MongoDB indexes on frequently queried fields (email, createdBy) make lookups fast even with millions of records.

3. **Clean Architecture**: Separation of concerns means you can optimize or replace individual components without touching everything else.

### Level 1: Vertical Scaling (The Easy Win)

**What it is**: Upgrade your server hardware - more CPU, more RAM, faster disk.

**When to use it**: When you're hitting 70-80% resource usage consistently.

**How to do it**:
```bash
# On AWS, upgrade your EC2 instance
# t2.micro → t2.small → t2.medium → t2.large

# On your VPS
# 1GB RAM → 2GB RAM → 4GB RAM → 8GB RAM
```

**Pros**: Simple, no code changes needed  
**Cons**: There's a ceiling - you can't scale infinitely  
**Cost**: $10/month → $40/month → $80/month

### Level 2: Horizontal Scaling with Load Balancer (The Real Deal)

**What it is**: Run multiple instances of your app behind a load balancer.


**Architecture Diagram**:
```
                    Internet
                       ↓
              [Load Balancer]
                       ↓
        ┌──────────────┼──────────────┐
        ↓              ↓              ↓
   [Server 1]     [Server 2]     [Server 3]
   Node.js        Node.js        Node.js
   Port 5002      Port 5002      Port 5002
        └──────────────┼──────────────┘
                       ↓
                  [MongoDB]
              (Single Instance)
```
### Level 4: Caching Layer (Speed Boost)

**Add Redis for frequently accessed data**:

```
    [Client Request]
           ↓
    [Load Balancer]
           ↓
      [Server 1]
           ↓
    Check Redis Cache?
      ↙         ↘
   Yes          No
    ↓            ↓
Return      Query MongoDB
Cached   →   Update Cache
Data          Return Data



### Database Scaling (When Data Gets Big)

**Problem**: Single MongoDB instance becomes a bottleneck.

**Solution 1: MongoDB Replica Set** (High Availability)

```
                [Primary]
                   ↓
        ┌──────────┼──────────┐
        ↓          ↓          ↓
   [Secondary] [Secondary] [Secondary]
   (Read)      (Read)      (Read)
```

**How it works**:
- Primary handles all writes
- Secondaries replicate data and handle reads
- If primary fails, a secondary becomes primary automatically




## What I Learned Building This

- JWT authentication and why it's perfect for scalable apps
- The importance of proper error handling (users hate cryptic errors!)
- How role-based access control works in practice
- Why API versioning matters from day one
- Database indexing can make or break performance
- Documentation is as important as code
- TypeScript catches so many bugs before they happen
- Scalability isn't just about handling more users - it's about architecture



just make it look good for the readme.md
