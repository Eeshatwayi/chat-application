# Real-Time Chat Application

A full-stack real-time chat application built with the MERN stack featuring WebSocket communication for instant messaging, chat rooms, and media sharing.

## Features

- Real-time messaging using Socket.io
- Create and join chat rooms for group conversations
- Private one-on-one messaging
- Send images and files
- Message persistence with chat history
- User authentication and authorization
- Responsive design

## Tech Stack

**Frontend:**
- React.js (v18.2.0)
- Socket.io-client (v4.6.0)
- Axios (v1.6.0)
- React Router DOM (v6.20.0)
- CSS3 / Styled Components

**Backend:**
- Node.js (v18.x or higher)
- Express.js (v4.18.0)
- Socket.io (v4.6.0)
- MongoDB (v6.0 or higher)
- Mongoose (v8.0.0)

**Authentication:**
- JSON Web Tokens (JWT)
- bcrypt.js

## 📋 Prerequisites

Before you begin, ensure you have the following installed on your system:

- **Node.js**: v18.x or higher ([Download here](https://nodejs.org/))
- **npm**: v9.x or higher (comes with Node.js)
- **MongoDB**: v6.0 or higher ([Download here](https://www.mongodb.com/try/download/community))
  - Or use MongoDB Atlas (cloud database)
- **Git**: For cloning the repository

To check your versions:
```bash
node --version
npm --version
mongo --version
```

## 🔧 Installation & Setup

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/chat-application.git
cd chat-application
```

### 2. Backend Setup

```bash
# Navigate to backend directory
cd backend

# Install dependencies
npm install

# Create .env file
touch .env
```

Add the following to your `.env` file:
```env
PORT=5000
MONGODB_URI=mongodb://localhost:27017/chatapp
JWT_SECRET=your_super_secret_jwt_key_here_change_this
NODE_ENV=development
CLIENT_URL=http://localhost:3000
```

**For MongoDB Atlas (Cloud Database):**
```env
MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/chatapp?retryWrites=true&w=majority
```

### 3. Frontend Setup

```bash
# Navigate to frontend directory (from root)
cd frontend

# Install dependencies
npm install

# Create .env file
touch .env
```

Add the following to your frontend `.env` file:
```env
REACT_APP_API_URL=http://localhost:5000
REACT_APP_SOCKET_URL=http://localhost:5000
```

### 4. Database Setup

**Option A: Local MongoDB**
```bash
# Start MongoDB service
# For Windows:
net start MongoDB

# For macOS (using Homebrew):
brew services start mongodb-community

# For Linux:
sudo systemctl start mongod
```

**Option B: MongoDB Atlas**
1. Create account at [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
2. Create a cluster
3. Get your connection string
4. Add to backend `.env` file

## 🚀 Running the Application

### Start Backend Server

```bash
# From backend directory
cd backend
npm start

# Or for development with auto-reload:
npm run dev
```

Server will run on `http://localhost:5000`

### Start Frontend Application

```bash
# From frontend directory (open new terminal)
cd frontend
npm start
```

Application will open automatically at `http://localhost:3000`

## 📁 Project Structure

```
chat-application/
├── backend/
│   ├── config/
│   │   └── db.js
│   ├── controllers/
│   │   ├── authController.js
│   │   ├── messageController.js
│   │   └── roomController.js
│   ├── middleware/
│   │   └── authMiddleware.js
│   ├── models/
│   │   ├── User.js
│   │   ├── Message.js
│   │   └── Room.js
│   ├── routes/
│   │   ├── authRoutes.js
│   │   ├── messageRoutes.js
│   │   └── roomRoutes.js
│   ├── uploads/
│   ├── socket/
│   │   └── socketHandler.js
│   ├── .env
│   ├── server.js
│   └── package.json
├── frontend/
│   ├── public/
│   ├── src/
│   │   ├── components/
│   │   │   ├── Auth/
│   │   │   ├── Chat/
│   │   │   ├── Rooms/
│   │   │   └── Common/
│   │   ├── contexts/
│   │   ├── services/
│   │   ├── utils/
│   │   ├── App.js
│   │   └── index.js
│   ├── .env
│   └── package.json
└── README.md
```

## Environment Variables

Backend .env:
- PORT - Server port number
- MONGODB_URI - MongoDB connection string
- JWT_SECRET - Secret key for JWT tokens
- NODE_ENV - Environment (development/production)
- CLIENT_URL - Frontend URL for CORS

Frontend .env:
- REACT_APP_API_URL - Backend API URL
- REACT_APP_SOCKET_URL - WebSocket server URL

## Troubleshooting

MongoDB Connection Error:
- Make sure MongoDB service is running
- Verify connection string in .env file
- For Atlas, check network access settings

Socket Connection Failed:
- Check if backend server is running
- Verify CORS settings in backend
- Ensure socket URL in frontend .env matches backend URL

Port Already in Use:
```bash
# Windows
netstat -ano | findstr :5000
taskkill /PID <PID> /F

# macOS/Linux
lsof -ti:5000 | xargs kill -9
```

## API Endpoints

Authentication:
- POST /api/auth/register - Register new user
- POST /api/auth/login - Login user
- GET /api/auth/me - Get current user

Messages:
- GET /api/messages/:roomId - Get room messages
- POST /api/messages - Send message
- POST /api/messages/upload - Upload media

Rooms:
- GET /api/rooms - Get all rooms
- POST /api/rooms - Create room
- GET /api/rooms/:id - Get room details

## Author

Eesha - https://github.com/Eeshatwayi

## Note

This project was created as part of an academic assignment to demonstrate real-time communication using the MERN stack and WebSockets.
