# 🚀 Launchpad

A full-stack web application for student onboarding, authentication, and test management built with **React + Vite** (frontend) and **Express + MongoDB** (backend).

🌐 **Live Deployment:**  
[Launchpad on Vercel](https://launchpadsfinal.vercel.app/mainpage)

---

## 📁 Folder Structure

```
project/
├── backend/       → Node.js + Express API
└── frontend/      → React + Vite app
```

---

## 🧪 Features

- User Signup & Login
- Admin Panel for control
- Student Dashboard
- Test instructions page
- MongoDB backend with JWT authentication
- Deployment-ready on Vercel

---

## ⚙️ Setup Guide

##### First fork the repo

```bash
git clone <your-github-repo-link>
cd Launchpad
```

### Setup for Backend

```env
cd backend
npm install
```

#### setup for the backend environment Variable

```env
cp .env.example .env
```

This is created a .env in the root folder of the backend which is contains this

```env
# MongoDB Database Configuration
MONGO_URI=mongodb+srv://<username>:<password>@cluster0.xxxxxx.mongodb.net/<databaseName>?retryWrites=true&w=majority

# JWT Configuration
JWT_SECRET=your_jwt_secret_key_here
PORT=5002

# Email (SMTP) Configuration
SMTP_EMAIL=your_email_here@gmail.com
SMTP_PASS=your_app_password_here

```

##### Run the Backend

```bash
npm run dev
```

---

### Setup for Frontend

Go to the frontend directory

```bash
cd frontend

npm install
```

#### setup for the frontend environment Variable

```bash
cp .env.example .env
```

##### This is created a .env inside the root folder of the frontend

```env
VITE_API_URL = https://launchpad-2.onrender.com
```

##### Run the frontend

```bash
npm run dev
```

#### Note

```bash
For best results and to avoid CORS issues, make sure your servers run on the following URLs:

Frontend → http://localhost:5173  
Backend  → http://localhost:5002
```

---

## 👨‍💻 Contributors
- Aamir Khan 
- Abhishek Kumar Chauhan  
-Devansh Verma  
