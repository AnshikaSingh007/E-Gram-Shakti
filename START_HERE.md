# 🎯 START HERE - E Gram Shakti

## 👥 Team Members

- **Anshika Singh**
- **Nidhi Kumari**
- **KumKum Kumari**
- **Neha Kumari**

## 🚀 Quick Start (5 Minutes)

### Step 1: Install Dependencies

```bash
# Frontend
cd frontend
npm install

# Backend (in new terminal)
cd backend
npm install
```

### Step 2: Create Environment Files

**Frontend** - Create `frontend/.env.local`:
```env
NEXT_PUBLIC_API_URL=http://localhost:3001/api
```

**Backend** - Create `backend/.env`:
```env
PORT=3001
```

### Step 3: Start Servers

**Terminal 1 - Backend:**
```bash
cd backend
npm run dev
```

**Terminal 2 - Frontend:**
```bash
cd frontend
npm run dev
```

### Step 4: Open Browser

Go to: http://localhost:3000

## 📚 Documentation Guide

### For Setup
👉 **[SETUP_GUIDE.md](./SETUP_GUIDE.md)** - Complete setup instructions

### For Problems
👉 **[PROBLEMS_AND_SOLUTIONS.md](./PROBLEMS_AND_SOLUTIONS.md)** - All problems and solutions

### For Deployment
👉 **[DEPLOY_TO_VERCEL.md](./DEPLOY_TO_VERCEL.md)** - Quick deployment guide
👉 **[VERCEL_DEPLOYMENT.md](./VERCEL_DEPLOYMENT.md)** - Detailed deployment guide

### For Team Members
👉 **[TEAM_GUIDE.md](./TEAM_GUIDE.md)** - Team collaboration guide

### For Project Info
👉 **[README.md](./README.md)** - Complete project overview

## ✅ Verification

After setup, verify:

1. **Backend Running:**
   ```bash
   curl http://localhost:3001/api/chatbot/health
   ```
   Should return: `{"status":"ok",...}`

2. **Frontend Running:**
   - Open http://localhost:3000
   - All pages should load

3. **Features Working:**
   - Voice assistant: http://localhost:3000/voice
   - Chatbot: http://localhost:3000/chatbot
   - Lessons: http://localhost:3000/lessons

## 🆘 Need Help?

1. Check [PROBLEMS_AND_SOLUTIONS.md](./PROBLEMS_AND_SOLUTIONS.md)
2. Review [SETUP_GUIDE.md](./SETUP_GUIDE.md)
3. Check terminal error messages
4. Ask team members

---

**Ready to start! Follow the steps above.** 🚀

*Team: Anshika Singh, Nidhi Kumari, KumKum Kumari, Neha Kumari*
