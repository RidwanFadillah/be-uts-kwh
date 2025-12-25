# Product Management API

A robust backend API for managing products and users, featuring role-based authentication and image uploads to AWS S3.

## Features

- **User Authentication**: Secure registration and login using JWT.
- **Role-Based Access Control (RBAC)**: Admin and User roles.
- **Product Management**: Create, Read, Update, and Delete (CRUD) operations for products.
- **Image Upload**: Upload product images directly to AWS S3.
- **Secure**: Password hashing with Bcrypt and protected routes.

## Tech Stack

- **Runtime**: Node.js
- **Framework**: Express.js
- **Database**: MySQL
- **Storage**: AWS S3
- **Authentication**: JWT (JSON Web Tokens)
- **Security**: Bcrypt, CORS

## Prerequisites

Before you begin, ensure you have the following installed:

- [Node.js](https://nodejs.org/) (v14 or higher recommended)
- [MySQL](https://www.mysql.com/)
- An [AWS Account](https://aws.amazon.com/) with an S3 bucket configured

## Installation

1. **Clone the repository:**

   ```bash
   git clone <repository-url>
   cd uts
   ```

2. **Install dependencies:**

   ```bash
   npm install
   ```

3. **Set up the database:**

   - Create a new MySQL database (e.g., `uts`).
   - Import the provided SQL dump file `uts.sql` into your database.

   ```bash
   mysql -u root -p uts < uts.sql
   ```

4. **Configure Environment Variables:**

   Create a `.env` file in the root directory and add the following variables:

   ```env
   PORT=3000

   # Database Configuration
   DB_HOST=localhost
   DB_USER=root
   DB_PASS=your_password
   DB_NAME=uts

   # AWS S3 Configuration
   AWS_REGION=your_aws_region
   AWS_ACCESS_KEY_ID=your_access_key_id
   AWS_SECRET_ACCESS_KEY=your_secret_access_key
   S3_BUCKET=your_s3_bucket_name

   # Security
   JWT_SECRET=your_jwt_secret_key
   ```

## Running the Application

- **Development Mode** (with hot-reload):

  ```bash
  npm run dev
  ```

- **Production Mode**:

  ```bash
  npm start
  ```

The server will start on `http://localhost:3000` (or your defined `PORT`).

## API Endpoints

### Authentication

- **POST** `/auth/register` - Register a new user.
- **POST** `/auth/login` - Login and receive a JWT token.

### Products

- **GET** `/products` - Retrieve all products.
- **POST** `/products` - Create a new product (Admin only, requires form-data with `image`).
- **PUT** `/products/:id` - Update an existing product (Admin only, requires form-data with `image`).
- **DELETE** `/products/:id` - Delete a product (Admin only).

## Project Structure

```
├── config/             # Database configuration
├── controllers/        # Route logic and controllers
├── middlewares/        # Custom middlewares (Auth, Admin, etc.)
├── models/             # Database models (implicit in SQL calls)
├── routes/             # API routes
├── server.js           # Entry point
└── uts.sql             # Database schema dump
```
