Taskify — To-Do App Backend (Express + MongoDB Atlas)

This is the backend API for Taskify, a simple to-do manager.
It supports user authentication with JWT and task management with categories.

🛠️ Tech Stack

Runtime: Node.js (ES Modules)

Framework: Express

Database: MongoDB Atlas (via Mongoose)

Authentication: JWT + bcrypt

⚙️ Setup

Create your environment file:

cp .env.example .env


Fill in the required values.

Install dependencies:

npm install


Start the dev server:

npm run dev

🌍 Environment Variables
Key	Description	Default
PORT	Port where the server runs	4000
MONGO_URI	MongoDB Atlas connection string	—
MONGO_DB_NAME	Name of your database (e.g. taskify)	—
JWT_SECRET	Long random string for signing JWTs	—
📌 API Endpoints
🔑 Auth

Register
POST /auth/register
Body:

{ "name": "Alice", "email": "alice@test.com", "password": "secret123" }


Response: 201 Created

Login
POST /auth/login
Body:

{ "email": "alice@test.com", "password": "secret123" }


Response:

{ "token": "<jwt>" }

✅ Tasks (requires Bearer token)

Get Tasks
GET /tasks?category=work

Create Task
POST /tasks
Body:

{ "title": "Buy groceries", "description": "Milk", "category": "personal" }


Update Task
PATCH /tasks/:id
Body (partial update):

{ "isDone": true }


Delete Task
DELETE /tasks/:id

📂 Project Structure
src/
  config/db.js
  controllers/
    authController.js
    taskController.js
  middleware/auth.js
  models/
    User.js
    Task.js
  routes/
    authRoutes.js
    taskRoutes.js
  app.js
  server.js

📝 Notes
Timestamps include only createdAt as per requirements.
Passwords are hashed with bcrypt.
JWTs expire after 7 days.