# 💬 Real-Time Chat Application

A **real-time chat app** built with the **MERN Stack**, **Socket.io**, **TailwindCSS**, **DaisyUI**, and **Zustand**, featuring **JWT authentication**, **online presence indicators**, and a sleek, responsive UI.

---

## 🚀 Features

- ⚡ **Instant Messaging:** Real-time two-way communication using **Socket.io**.
- **Authentication:** Secure login & signup with **JWT tokens**.
- 🟢 **Online Status:** Track and display online/offline users dynamically.
- 🌐 **Cloud Storage:** Store and manage user images with **Cloudinary**.
- 🧠 **Global State Management:** Smooth UI updates with **Zustand**.
- 🎨 **Modern UI:** Responsive design using **TailwindCSS** & **DaisyUI**.
- 🧩 **Error Handling:** Robust client and server-side error management.

---

## 🧰 Tech Stack

| Category                   | Technologies                                           |
| -------------------------- | ------------------------------------------------------ |
| **Frontend**         | React, Zustand, TailwindCSS, DaisyUI, Socket.io-client |
| **Backend**          | Node.js, Express.js, MongoDB, Socket.io                |
| **Authentication**   | JWT (JSON Web Token)                                   |
| **Media Storage**    | Cloudinary                                             |
| **State Management** | Zustand                                                |
| **Environment**      | .env configuration                                     |

---

---

## ⚙️ Setup Guide

##### First fork the repo and then copy the link from your repo

```bash
git clone <your-github-repo-link>
cd ChatApp
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

This is created a .env in the root folder of the backend which is contains this automatically

```env
MONGODB_URI=

PORT=5001

JWT_SECRET=mysecretkey

NODE_ENV=development

CLOUDINARY_CLOUD_NAME=
CLOUDINARY_API_KEY=
CLOUDINARY_API_SECRET=

FRONTEND_URL=
SENDER_EMAIL =
BREVO_API_KEY=

```

##### Run the Backend

```bash
npm run dev
```

---

### Setup for Frontend

Go to the frontend directory

```bash
cd ..

cd frontend

npm install
```
#### setup for the frontend environment Variable

```bash
cp .env.example .env
```

##### This is created a .env inside the root folder of the frontend

```env
VITE_GOOGLE_CLIENT_ID=
VITE_BACKEND_URL=

VITE_GIPHY_API= 
```

##### Run the frontend

```bash
npm run dev
```

#### Note

```bash
For best results and to avoid CORS issues, make sure your servers run on the following URLs:

Frontend → http://localhost:5173  
Backend  → http://localhost:5001
```

----
### Installation

**Option 1: Run with Docker**

1. **Build and run the Docker containers**
   ```bash
   docker-compose up --build
   ```
2. **Access the application**
   - Frontend: http://localhost:5173
   - Backend: http://localhost:5001

**Option 2: Run both servers manually**

```bash

cd backend
npm install

cd frontend
npm install

cd backend
npm run dev

cd frontend
npm run dev

```

**Access the application**

- Frontend: http://localhost:5173
- Backend: http://localhost:5001
