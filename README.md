Node.js Practical Exam – User Registration & Login
📌 Project Overview

This project is a Node.js practical application that demonstrates how to create and manage user data and implement a basic user login system.

The application allows users to:

Register a new account

Store user information

Log in using their registered credentials

Validate login credentials

Receive appropriate success and error responses

🛠️ Technologies Used

Node.js – JavaScript runtime environment

Express.js – Web application framework

MongoDB – Database for storing user information

Mongoose – MongoDB object modeling library

bcrypt.js – Password hashing

JSON / REST API – Data communication

dotenv – Environment variable management

📁 Project Structure
nodejs-user-auth/
│
├── controllers/
│   └── userController.js
│
├── models/
│   └── User.js
│
├── routes/
│   └── userRoutes.js
│
├── middleware/
│   └── authMiddleware.js
│
├── .env
├── .gitignore
├── package.json
├── package-lock.json
├── server.js
└── README.md

🚀 Installation
1. Clone the project
git clone <repository-url>
cd nodejs-user-auth

2. Install dependencies
npm install

3. Create .env file

Create a .env file in the root directory:

PORT=5000
MONGO_URI=mongodb://127.0.0.1:27017/user_auth
JWT_SECRET=your_secret_key


Replace the MongoDB connection string and secret key according to your environment.

4. Start the server

For normal execution:

node server.js


For development using Nodemon:

npm run dev


The server will run at:

http://localhost:5000

👤 User Data

The user collection stores information such as:

{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "hashed_password"
}


Passwords should never be stored as plain text. The password is hashed before being saved to the database.

🔐 User Registration
Endpoint
POST /api/users/register

Request Body
{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "123456"
}

Process

Receive user registration data.

Validate the required fields.

Check whether the email already exists.

Hash the password using bcrypt.

Save the user information to MongoDB.

Return a success response.

Example Response
{
  "message": "User registered successfully"
}

🔑 User Login
Endpoint
POST /api/users/login

Request Body
{
  "email": "john@example.com",
  "password": "123456"
}

Process

Receive the email and password.

Find the user using the email.

Compare the entered password with the stored hashed password.

If the credentials are valid, allow the user to log in.

Return an authentication response.

Example Response
{
  "message": "Login successful"
}

❌ Error Handling
User Already Exists
{
  "message": "User already exists"
}

Invalid Login Credentials
{
  "message": "Invalid email or password"
}

Missing Required Fields
{
  "message": "All fields are required"
}

🧪 Testing the API

The APIs can be tested using tools such as Postman, Thunder Client, or any REST API client.

Test Registration
POST http://localhost:5000/api/users/register


Body:

{
  "name": "Test User",
  "email": "test@example.com",
  "password": "password123"
}

Test Login
POST http://localhost:5000/api/users/login


Body:

{
  "email": "test@example.com",
  "password": "password123"
}

📋 Practical Exam Requirements

The practical demonstrates the following concepts:

Creating a Node.js project

Installing and using npm packages

Creating an Express server

Connecting Node.js with MongoDB

Creating a Mongoose user model

Creating REST API routes

Registering users

Hashing passwords

Validating login credentials

Handling errors

Testing APIs using Postman

🔄 Application Flow
              ┌──────────────┐
              │     User     │
              └──────┬───────┘
                     │
             Registration/Login
                     │
                     ▼
              ┌──────────────┐
              │   Express    │
              │    Server    │
              └──────┬───────┘
                     │
                     ▼
              ┌──────────────┐
              │ User Routes  │
              └──────┬───────┘
                     │
                     ▼
              ┌──────────────┐
              │  Controller  │
              └──────┬───────┘
                     │
                     ▼
              ┌──────────────┐
              │   MongoDB    │
              └──────────────┘

🔒 Security Considerations

Never store passwords in plain text.

Use bcrypt or another secure password-hashing algorithm.

Store sensitive configuration values in .env.

Do not upload .env to GitHub.

Validate user input before storing it in the database.

Use appropriate HTTP status codes for errors and successful requests.

📦 Example package.json Scripts
{
  "scripts": {
    "start": "node server.js",
    "dev": "nodemon server.js"
  }
}

✅ Expected Result

After completing the practical:

A user can register with their name, email, and password.

User information is stored in MongoDB.

The password is stored securely as a hash.

A registered user can log in with valid credentials.

Invalid credentials return an appropriate error.

The APIs can be tested successfully using Postman.

👨‍💻 Conclusion

This practical demonstrates the basic implementation of user registration and login authentication using Node.js, Express.js, and MongoDB. It provides a foundation for building more advanced authentication systems and REST APIs.
