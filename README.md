# Bookstore App - System Design

This repository contains the system design for a **Bookstore App** built with **React Native** for the frontend and **MERN stack** (MongoDB, Express, React, Node.js) for the backend. The app is hosted on **AWS** with **AWS S3** for media storage.

## Table of Contents

1. [Frontend (React Native)](#1-frontend-react-native)
2. [Backend (API)](#2-backend-api)
3. [Database (MongoDB)](#3-database-mongodb)
4. [Authentication](#4-authentication)
5. [Cloud Storage (AWS S3)](#5-cloud-storage-aws-s3)
6. [Server and Deployment](#6-server-and-deployment)
7. [API Endpoints](#7-api-endpoints)
8. [Example Flow](#8-example-flow)
9. [Hosting and Deployment](#9-hosting-and-deployment)
10. [Development Timeline](#10-development-timeline)

## 1. Frontend (React Native)

- **User Interface**: Mobile app (iOS/Android)
  - **Home Page**: List of Books
  - **Authentication**: Login/Signup
  - **Profile Page**
  - **Book CRUD**: Add, Update, Delete, View
  - **Search**: By title, author, genre
  - **Book Details**: Description, Ratings

## 2. Backend (API)

- **Node.js with Express** for API server
- **Authentication**:
  - JWT-based (Login, Signup, Logout)
  - OAuth for Google/Facebook logins
- **APIs**:
  - **User Management**: Register, Login, Profile management, Password reset
  - **Book Management**: Add, Update, Delete, View, Search Books
  - **Media**: Upload Book Cover Images
  - **User Interactions**: Rate, Like, Follow Recommendations

## 3. Database (MongoDB)

- **Users Collection**:
  - `user_id`, `name`, `email`, `password_hash`, `profile_picture_url`, `recommendations`, `bookmarked_books`
- **Books Collection**:
  - `book_id`, `title`, `author`, `description`, `cover_image_url`, `rating`, `genres`
- **Recommendations Collection**:
  - `recommendation_id`, `user_id`, `book_id`, `created_at`
- **Ratings Collection**:
  - `rating_id`, `book_id`, `user_id`, `rating`
- **Media Collection**:
  - `file_id`, `book_id`, `media_url`

## 4. Authentication

- **JWT Authentication**: Secure access with JWT tokens.
  - On successful login/registration, a JWT token is generated.
  - Tokens are passed in headers for protected routes.
- **Role-based Access Control (RBAC)**:
  - Admin can manage books and users, while regular users interact with books.

## 5. Cloud Storage (AWS S3)

- **AWS S3** for storing images (book covers, profile pictures).
  - Frontend uploads images; backend stores URLs in the database.

## 6. Server and Deployment

- **Node.js/Express** hosted on **AWS EC2** or **Heroku**.
- **MongoDB**: Hosted on **MongoDB Atlas** or self-hosted on AWS.
- **CI/CD**: GitHub Actions or CircleCI for deployment automation.

## 7. API Endpoints

### Authentication
- `POST /api/auth/register` – Register
- `POST /api/auth/login` – Login
- `POST /api/auth/logout` – Logout
- `POST /api/auth/refresh-token` – Refresh JWT

### User Management
- `GET /api/user/profile` – Get profile
- `PUT /api/user/profile` – Update profile
- `POST /api/user/change-password` – Change password

### Books
- `GET /api/books` – List all books
- `POST /api/books/recommend` – Create recommendation
- `GET /api/books/{id}` – Get book details
- `POST /api/books/{id}/rating` – Rate a book

### Search
- `GET /api/search` – Search books by title, author, genre

## 8. Example Flow

- **Frontend** sends requests to the backend using REST APIs.
- **Backend** handles authentication, user management, book operations, and stores data in MongoDB.
- Media files (cover images) are uploaded to **AWS S3**, and URLs are stored in the database.

## 9. Hosting and Deployment

- **Frontend** (React Native) connects to the backend hosted on **AWS EC2**.
- **Backend** uses **Node.js** and **MongoDB** (Atlas).
- **AWS S3** is used for storing media files.
- **CI/CD** is managed using GitHub Actions or CircleCI.

## 10. Development Timeline

1. **Week 1-2**: Set up backend (Node.js, Express, MongoDB, JWT).
2. **Week 3-4**: Implement authentication APIs (Login, Signup, JWT).
3. **Week 5-6**: Develop CRUD APIs for books, profile management, media upload.
4. **Week 7-8**: Integrate React Native frontend with the backend.
5. **Week 9-10**: Testing, deployment, performance optimization.

---

This design focuses on building a scalable, secure, and efficient system for your bookstore app with key components for authentication, book management, media handling, and cloud deployment.
