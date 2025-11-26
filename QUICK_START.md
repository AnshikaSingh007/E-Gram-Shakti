# ⚡ Quick Start Guide

## One-Command Setup

```bash
# Install all dependencies
cd backend && npm install && cd ../frontend && npm install && cd ..
```

## Start Project

### Option 1: Separate Terminals (Recommended)

**Terminal 1:**
```bash
cd backend && npm run dev
```

**Terminal 2:**
```bash
cd frontend && npm run dev
```

### Option 2: Single Command (if root package.json exists)

```bash
npm run dev
```

## Access

- **Frontend**: http://localhost:3000
- **Backend API**: http://localhost:3001/api
- **Health Check**: http://localhost:3001/api/health

## Project Structure

```
backend/          → NestJS API (Port 3001)
frontend/         → Next.js App (Port 3000)
```

## Features

- 🏠 Home Page
- 📊 Admin Panel (`/admin`)
- 📈 Dashboard (`/dashboard`)
- 📚 Lessons (`/lessons`)
- 🏛️ Schemes (`/schemes`)
- 🏥 Healthcare (`/healthcare`)
- 🌾 Market (`/market`)
- 💳 Payments (`/payments`)
- 🎤 Voice Assistant (`/voice`)

## Test Backend

```bash
curl http://localhost:3001/api/health
curl http://localhost:3001/api/lessons
curl http://localhost:3001/api/schemes
```

## Troubleshooting

**Backend not starting?**
```bash
pkill -f "tsx.*backend"
cd backend && npm run dev
```

**Frontend not starting?**
```bash
pkill -f "next"
cd frontend && npm run dev
```

**Ports in use?**
```bash
lsof -ti:3001 | xargs kill -9
lsof -ti:3000 | xargs kill -9
```

---

✅ **Ready!** Open http://localhost:3000

