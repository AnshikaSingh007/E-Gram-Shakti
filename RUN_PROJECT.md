# 🚀 Run Project - Complete Guide

## Quick Start (2 Steps)

### Step 1: Start Backend
```bash
cd backend
npm run dev
```
**Backend runs on:** http://localhost:3001/api

### Step 2: Start Frontend (New Terminal)
```bash
cd frontend
npm run dev
```
**Frontend runs on:** http://localhost:3000

## Verify Everything is Working

### Check Backend
```bash
curl http://localhost:3001/api/chatbot/health
```
Should return: `{"status":"ok","service":"chatbot",...}`

### Check Frontend
Open browser: http://localhost:3000

## Features Available

✅ **Chatbot** - `/chatbot` (Gemini AI powered)
✅ **Voice Assistant** - `/voice` (Multilingual)
✅ **Lessons** - `/lessons`
✅ **Test** - `/test`
✅ **Progress** - `/progress`
✅ **Schemes** - `/schemes`
✅ **Healthcare** - `/healthcare`
✅ **Market** - `/market`
✅ **Payments** - `/payments`
✅ **Dashboard** - `/dashboard`
✅ **Admin** - `/admin`

## Optional: Gemini AI Setup

1. Get API key from: https://makersuite.google.com/app/apikey
2. Create `backend/.env`:
   ```
   GEMINI_API_KEY=your_key_here
   ```
3. Restart backend

## Troubleshooting

### Backend Not Starting
```bash
# Kill old processes
pkill -9 -f "tsx.*backend"

# Clear cache
cd backend
rm -rf node_modules/.cache .cache

# Restart
npm run dev
```

### Port Already in Use
```bash
# Kill process on port 3001
lsof -ti:3001 | xargs kill -9

# Kill process on port 3000
lsof -ti:3000 | xargs kill -9
```

### Chatbot Not Working
- Backend works without Gemini API key (uses local detection)
- Add `GEMINI_API_KEY` to `backend/.env` for AI responses
- Check backend is running: `curl http://localhost:3001/api/chatbot/health`

## Status Check

```bash
# Check backend
curl http://localhost:3001/api/chatbot/health

# Check frontend
curl http://localhost:3000
```

Both should return valid responses!
