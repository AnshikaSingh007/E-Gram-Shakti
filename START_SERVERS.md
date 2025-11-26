# How to Start Frontend and Backend

## 🚀 Quick Start

### Option 1: Start Both Together (Recommended)
```bash
cd /Users/akashsingh/Downloads/Nidhi
npm run dev
```
This starts both frontend and backend concurrently.

### Option 2: Start Separately

#### Start Backend
```bash
cd backend
npm run dev
```
Backend runs on: `http://localhost:3001/api`

#### Start Frontend (in new terminal)
```bash
cd frontend
npm run dev
```
Frontend runs on: `http://localhost:3000`

## ✅ Verification

### Check Backend
```bash
curl http://localhost:3001/api/health
```
Should return: `{"status":"ok"}`

### Check Frontend
Open browser: `http://localhost:3000`

### Check API Connection
```bash
curl http://localhost:3001/api/analytics/summary
```
Should return JSON with statistics.

## 🔗 Access Points

- **Frontend**: http://localhost:3000
- **Backend API**: http://localhost:3001/api
- **Admin Panel**: http://localhost:3000/admin
- **Dashboard**: http://localhost:3000/dashboard

## 📊 Admin Panel

Access at: `http://localhost:3000/admin`

Features:
- Overview tab with statistics
- Users tab for user management
- Analytics tab with charts
- Content tab with quick links
- CSV export functionality
- Village filtering

## 🔧 Troubleshooting

### Backend not starting?
1. Check if port 3001 is available
2. Check backend/.env file exists
3. Run `npm install` in backend directory

### Frontend not starting?
1. Check if port 3000 is available
2. Run `npm install` in frontend directory
3. Clear `.next` directory if needed

### API connection issues?
1. Verify backend is running on port 3001
2. Check CORS settings in backend
3. Verify API_BASE_URL in frontend

## ✅ System Ready When:

- ✅ Backend responds on port 3001
- ✅ Frontend responds on port 3000
- ✅ Admin panel loads at /admin
- ✅ API calls return data
- ✅ All navigation links work

