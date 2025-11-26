# Quick Setup Guide

## Issues Fixed

✅ Backend ConfigService injection error - Fixed
✅ Frontend lock file issue - Fixed
✅ Port conflicts - Handled

## Environment Variables Setup

### Backend (.env file in `/backend` directory)

Create `backend/.env`:

```env
SUPABASE_URL=your_supabase_url_here
SUPABASE_ANON_KEY=your_supabase_anon_key_here
PORT=3001
FRONTEND_URL=http://localhost:3000
```

**Note**: For development, you can leave Supabase credentials empty. The backend will start but will show a warning. You'll need to provide real credentials when using database features.

### Frontend (.env.local file in `/frontend` directory)

Create `frontend/.env.local`:

```env
NEXT_PUBLIC_SUPABASE_URL=your_supabase_url_here
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key_here
```

## Running the Application

### Option 1: Run Both Together (Recommended)

From the root directory:
```bash
npm run dev
```

This will start:
- Frontend on http://localhost:3000
- Backend on http://localhost:3001

### Option 2: Run Separately

**Frontend only:**
```bash
npm run dev:frontend
# or
cd frontend && npm run dev
```

**Backend only:**
```bash
npm run dev:backend
# or
cd backend && npm run dev
```

## Troubleshooting

### Port 3000 Already in Use

If port 3000 is already in use:
1. Kill the process: `lsof -ti:3000 | xargs kill -9`
2. Or the app will automatically use port 3001

### Next.js Lock File Error

If you see a lock file error:
```bash
cd frontend
rm -rf .next
npm run dev
```

### Backend Supabase Error

If you see Supabase errors:
1. Make sure you have `backend/.env` file with Supabase credentials
2. Or leave them empty for development (features will be limited)

## Next Steps

1. Set up Supabase project at https://supabase.com
2. Run the database migration from `infra/database.sql`
3. Add your Supabase credentials to `.env` files
4. Restart the servers

## Development Without Supabase

The app can run in development mode without Supabase:
- Frontend will work with offline storage
- Backend will start but database features won't work
- You can test UI/UX features without database

