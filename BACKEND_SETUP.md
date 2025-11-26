# Backend Setup Guide

## Overview
The backend is built with NestJS and provides RESTful API endpoints for the E Gram Shakti application.

## Features
- **Users API**: User management, progress tracking, digital card generation
- **Lessons API**: Lesson content management and completion tracking
- **Schemes API**: Government schemes information with filtering
- **Analytics API**: Village statistics, literacy distribution, adoption rates
- **Tests API**: Digital literacy test questions and result submission
- **Sample Data**: Automatic seeding of sample data on startup

## Setup Instructions

### 1. Install Dependencies
```bash
cd backend
npm install
```

### 2. Configure Environment Variables
Create a `.env` file in the `backend` directory:
```env
SUPABASE_URL=your_supabase_url_here
SUPABASE_ANON_KEY=your_supabase_anon_key_here
PORT=3001
FRONTEND_URL=http://localhost:3000
```

### 3. Set Up Database
Run the SQL schema from `infra/database.sql` in your Supabase SQL editor.

### 4. Run the Backend
```bash
# Development mode (with hot reload)
npm run dev

# Production mode
npm run build
npm start
```

The backend will start on `http://localhost:3001`

## API Endpoints

### Users
- `GET /api/users` - Get all users (optional query: `?village=name`)
- `GET /api/users/:id` - Get user by ID
- `POST /api/users` - Create new user
- `PUT /api/users/:id` - Update user
- `GET /api/users/:id/progress` - Get user progress
- `PUT /api/users/:id/progress` - Update user progress
- `GET /api/users/:id/card` - Get user digital card

### Lessons
- `GET /api/lessons` - Get all lessons
- `GET /api/lessons/:id` - Get lesson by ID
- `POST /api/lessons` - Create lesson
- `PUT /api/lessons/:id` - Update lesson
- `POST /api/lessons/:id/complete` - Mark lesson as complete

### Schemes
- `GET /api/schemes` - Get all schemes (optional query: `?category=name`)
- `GET /api/schemes/:id` - Get scheme by ID
- `POST /api/schemes` - Create scheme
- `PUT /api/schemes/:id` - Update scheme

### Analytics
- `GET /api/analytics/summary` - Get overall summary statistics
- `GET /api/analytics/villages` - Get village statistics (optional query: `?village=name`)
- `GET /api/analytics/literacy-distribution` - Get literacy score distribution
- `GET /api/analytics/adoption-rate` - Get adoption rates by village

### Tests
- `GET /api/tests/questions` - Get test questions
- `POST /api/tests/submit` - Submit test answers
- `GET /api/tests/result/:userId` - Get test result for user

## Sample Data
The backend automatically seeds sample data on startup if the database is empty:
- Sample users (3 users across 3 villages)
- Sample lessons (4 lessons)
- Sample government schemes (6 schemes)

## CORS Configuration
CORS is enabled for `http://localhost:3000` by default. Update `FRONTEND_URL` in `.env` if your frontend runs on a different port.

## Error Handling
All endpoints include proper error handling and will return appropriate HTTP status codes:
- `200` - Success
- `400` - Bad Request
- `404` - Not Found
- `500` - Internal Server Error

## Offline Support
The backend is designed to work with the frontend's offline-first approach. When the backend is unavailable, the frontend will gracefully fall back to local storage.

