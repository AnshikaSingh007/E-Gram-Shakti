# 🚀 How to Run E Gram Shakti Project

## Quick Setup (3 Steps)

### 1️⃣ Install Dependencies

```bash
# Backend
cd backend
npm install

# Frontend (new terminal)
cd frontend  
npm install
```

### 2️⃣ Start Backend

```bash
cd backend
npm run dev
```
✅ **Backend**: http://localhost:3001/api

### 3️⃣ Start Frontend

```bash
cd frontend
npm run dev
```
✅ **Frontend**: http://localhost:3000

---

## 📁 Project Structure

```
Nidhi/
├── backend/              # NestJS API (Port 3001)
│   └── src/
│       ├── analytics/    # Statistics
│       ├── healthcare/    # Health services
│       ├── lessons/      # Digital lessons
│       ├── market/       # Market info
│       ├── payments/     # Payments
│       ├── schemes/      # Govt schemes
│       ├── users/        # User management
│       └── main.ts       # Entry point
│
└── frontend/             # Next.js App (Port 3000)
    └── app/
        ├── admin/        # Admin panel
        ├── dashboard/    # Analytics
        ├── lessons/      # Lessons page
        ├── schemes/       # Schemes page
        ├── healthcare/    # Healthcare page
        ├── market/        # Market page
        ├── payments/     # Payments page
        └── voice/         # Voice assistant
```

## 🔌 API Endpoints

**Base**: `http://localhost:3001/api`

- `GET /health` - Health check
- `GET /analytics/summary` - Statistics
- `GET /lessons` - All lessons
- `GET /schemes` - All schemes
- `GET /healthcare/services` - Health services
- `GET /market/prices` - Market prices
- `GET /payments/methods/:userId` - Payment methods

## 📋 Available Pages

- `/` - Home
- `/admin` - Admin panel
- `/dashboard` - Analytics
- `/lessons` - Digital lessons
- `/schemes` - Government schemes
- `/healthcare` - Health services
- `/market` - Market information
- `/payments` - Digital payments
- `/voice` - Voice assistant

## ✅ Verify Installation

```bash
# Test backend
curl http://localhost:3001/api/health

# Test lessons
curl http://localhost:3001/api/lessons
```

## 🔧 Troubleshooting

**Port in use?**
```bash
# Kill backend
pkill -f "tsx.*backend"

# Kill frontend
pkill -f "next"
```

**Module errors?**
```bash
# Reinstall
cd backend && rm -rf node_modules && npm install
cd frontend && rm -rf node_modules && npm install
```

**API not working?**
- Ensure backend starts before frontend
- Check both terminals for errors
- Verify ports 3000 and 3001 are free

## 📝 Environment (Optional)

Create `backend/.env`:
```env
PORT=3001
FRONTEND_URL=http://localhost:3000
```

**Note**: Works without .env - uses sample data.

## 🎯 Quick Test

1. ✅ Backend running → http://localhost:3001/api/health
2. ✅ Frontend running → http://localhost:3000
3. ✅ Admin panel → http://localhost:3000/admin

---

**Status**: ✅ Ready to use!

