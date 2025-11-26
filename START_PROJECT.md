# 🚀 How to Start the Project

## Prerequisites
- Node.js v20+ installed
- npm installed

## Step 1: Start Backend

```bash
cd backend
npm install  # if not already done
npm run dev
```

Backend will run on: **http://localhost:3001/api**

## Step 2: Start Frontend (in a new terminal)

```bash
cd frontend
npm install  # if not already done
npm run dev
```

Frontend will run on: **http://localhost:3000**

## Step 3: Access the Application

1. Open browser: http://localhost:3000
2. Navigate to Admin Panel: http://localhost:3000/admin
3. Check all features:
   - Home page
   - Lessons
   - Schemes
   - Healthcare
   - Market
   - Payments
   - Dashboard
   - Voice Assistant

## Troubleshooting

### Backend not starting?
- Check if port 3001 is available
- Kill existing processes: `pkill -f "tsx.*backend"`
- Check logs in terminal

### Frontend not starting?
- Check if port 3000 is available
- Kill existing processes: `pkill -f "next"`
- Check logs in terminal

### API errors?
- Ensure backend is running first
- Check browser console for errors
- Verify API URL in `frontend/lib/api.ts`

## Current Status

✅ **Backend**: Running and routes mapped
✅ **Frontend**: Ready to connect
⚠️ **Services**: May need restart if dependency injection issues occur

## Quick Test

```bash
# Test backend health
curl http://localhost:3001/api/health

# Test analytics
curl http://localhost:3001/api/analytics/summary

# Test lessons
curl http://localhost:3001/api/lessons
```

All endpoints should return JSON data.

