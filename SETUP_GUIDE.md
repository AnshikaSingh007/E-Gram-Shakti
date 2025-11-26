# 📖 Complete Setup Guide - E Gram Shakti

## 👥 Team Members

- **Anshika Singh**
- **Nidhi Kumari**
- **KumKum Kumari**
- **Neha Kumari**

## 📋 Table of Contents

1. [Prerequisites](#prerequisites)
2. [Initial Setup](#initial-setup)
3. [Environment Configuration](#environment-configuration)
4. [Running the Project](#running-the-project)
5. [Common Problems & Solutions](#common-problems--solutions)
6. [Deployment](#deployment)

## 🔧 Prerequisites

Before starting, ensure you have:

### Required Software
- **Node.js** (v20 or higher)
  - Download: https://nodejs.org/
  - Verify: `node --version`
- **npm** (comes with Node.js)
  - Verify: `npm --version`
- **Git**
  - Download: https://git-scm.com/
  - Verify: `git --version`

### Optional Software
- **VS Code** (Recommended IDE)
- **Postman** (For API testing)

## 🚀 Initial Setup

### Step 1: Clone the Repository

```bash
# Clone the repository
git clone <repository-url>

# Navigate to project directory
cd Nidhi
```

### Step 2: Install Frontend Dependencies

```bash
# Navigate to frontend directory
cd frontend

# Install all dependencies
npm install

# This will install:
# - Next.js 16
# - React 19
# - TypeScript
# - Tailwind CSS
# - And all other frontend dependencies
```

**Expected Output:**
```
added 500+ packages in 30s
```

### Step 3: Install Backend Dependencies

```bash
# Navigate to backend directory (from project root)
cd ../backend

# Install all dependencies
npm install

# This will install:
# - NestJS 11
# - TypeScript
# - Express
# - And all other backend dependencies
```

**Expected Output:**
```
added 200+ packages in 20s
```

## ⚙️ Environment Configuration

### Frontend Environment Variables

Create `frontend/.env.local` file:

```bash
cd frontend
touch .env.local
```

Add the following content:

```env
# Backend API URL
# For local development, use localhost
# For production, use your deployed backend URL
NEXT_PUBLIC_API_URL=http://localhost:3001/api

# Supabase Configuration (Optional - only if using Supabase)
NEXT_PUBLIC_SUPABASE_URL=your_supabase_url_here
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key_here
```

**Important Notes:**
- `NEXT_PUBLIC_` prefix makes variables available in browser
- Use `http://localhost:3001/api` for local development
- Replace with production URL when deploying

### Backend Environment Variables

Create `backend/.env` file:

```bash
cd backend
touch .env
```

Add the following content:

```env
# Server Port
PORT=3001

# Gemini AI API Key (Optional - for enhanced chatbot)
# Get from: https://makersuite.google.com/app/apikey
GEMINI_API_KEY=your_gemini_api_key_here

# Supabase Configuration (Optional - only if using Supabase)
SUPABASE_URL=your_supabase_url_here
SUPABASE_ANON_KEY=your_supabase_anon_key_here
```

**Important Notes:**
- Backend works without Gemini API key (uses local detection)
- Backend works without Supabase (uses sample data)
- Port 3001 is default, change if needed

## 🏃 Running the Project

### Development Mode

You need **two terminal windows** - one for backend, one for frontend.

#### Terminal 1: Start Backend

```bash
# Navigate to backend directory
cd backend

# Start development server
npm run dev
```

**Expected Output:**
```
[Nest] Starting Nest application...
Backend server running on http://localhost:3001/api
```

**✅ Success Indicators:**
- No error messages
- "Backend server running" message appears
- Port 3001 is listening

#### Terminal 2: Start Frontend

```bash
# Navigate to frontend directory
cd frontend

# Start development server
npm run dev
```

**Expected Output:**
```
▲ Next.js 16.0.4
- Local:        http://localhost:3000
- Ready in 2.5s
```

**✅ Success Indicators:**
- No error messages
- "Ready" message appears
- Port 3000 is listening

### Verify Everything Works

1. **Open Browser:**
   - Go to: http://localhost:3000
   - You should see the E Gram Shakti homepage

2. **Test Backend:**
   ```bash
   curl http://localhost:3001/api/chatbot/health
   ```
   Should return: `{"status":"ok","service":"chatbot",...}`

3. **Test Frontend Pages:**
   - Home: http://localhost:3000
   - Voice: http://localhost:3000/voice
   - Chatbot: http://localhost:3000/chatbot
   - Lessons: http://localhost:3000/lessons
   - Schemes: http://localhost:3000/schemes

## 🐛 Common Problems & Solutions

### Problem 1: "Cannot find module" Error

**Error Message:**
```
Error: Cannot find module 'xxx'
```

**Solution:**
```bash
# Delete node_modules and reinstall
rm -rf node_modules package-lock.json
npm install
```

### Problem 2: Backend Won't Start

**Error Message:**
```
TypeError: Cannot read properties of undefined
```

**Solution:**
```bash
cd backend

# Clear cache
rm -rf node_modules/.cache .cache dist

# Reinstall dependencies
npm install

# Restart
npm run dev
```

### Problem 3: Port Already in Use

**Error Message:**
```
Error: listen EADDRINUSE: address already in use :::3001
```

**Solution:**
```bash
# Option 1: Kill the process using the port
lsof -ti:3001 | xargs kill -9

# Option 2: Use a different port
# In backend/.env, change:
PORT=3002
```

### Problem 4: Frontend Build Fails

**Error Message:**
```
Type error: ...
Failed to compile
```

**Solution:**
```bash
cd frontend

# Clear Next.js cache
rm -rf .next

# Rebuild
npm run build
```

### Problem 5: API Connection Failed

**Error Message:**
```
Failed to fetch
Network Error
```

**Solution:**
1. **Check Backend is Running:**
   ```bash
   curl http://localhost:3001/api/chatbot/health
   ```

2. **Check Environment Variable:**
   - Verify `NEXT_PUBLIC_API_URL` in `frontend/.env.local`
   - Should be: `http://localhost:3001/api`

3. **Check CORS:**
   - Backend should allow `http://localhost:3000`
   - Check `backend/src/main.ts` CORS configuration

### Problem 6: Service Worker Not Working

**Error Message:**
```
Service Worker registration failed
```

**Solution:**
1. **Check HTTPS/Production:**
   - Service workers work best in production
   - For local testing, use `npm run build && npm start`

2. **Check File Exists:**
   - Verify `/public/sw.js` exists
   - Check browser console for errors

### Problem 7: TypeScript Errors

**Error Message:**
```
Type error: Property 'xxx' does not exist
```

**Solution:**
```bash
# Check TypeScript compilation
cd frontend
npx tsc --noEmit

# Fix type errors or add type assertions
# Example: (variable as any).property
```

## 🌐 Deployment

### Frontend Deployment (Vercel)

**Quick Steps:**
1. Install Vercel CLI: `npm install -g vercel`
2. Deploy: `cd frontend && vercel`
3. Set environment variables in Vercel dashboard

**Detailed Guide:** See [DEPLOY_TO_VERCEL.md](./DEPLOY_TO_VERCEL.md)

### Backend Deployment

**Recommended Platforms:**
- **Railway.app** (Easiest)
- **Render.com**
- **Fly.io**

**Steps:**
1. Create account on chosen platform
2. Connect GitHub repository
3. Set root directory to `backend`
4. Add environment variables
5. Deploy

**Detailed Guide:** See [VERCEL_DEPLOYMENT.md](./VERCEL_DEPLOYMENT.md)

## 📝 Next Steps After Setup

1. **Explore the Application:**
   - Test all pages
   - Try voice assistant
   - Test chatbot
   - Check offline functionality

2. **Customize:**
   - Update content in pages
   - Modify styles in `globals.css`
   - Add new features

3. **Deploy:**
   - Deploy backend first
   - Deploy frontend to Vercel
   - Set environment variables
   - Test production site

## ✅ Setup Verification Checklist

- [ ] Node.js installed (v20+)
- [ ] Repository cloned
- [ ] Frontend dependencies installed
- [ ] Backend dependencies installed
- [ ] Frontend `.env.local` created
- [ ] Backend `.env` created
- [ ] Backend starts without errors
- [ ] Frontend starts without errors
- [ ] Can access http://localhost:3000
- [ ] Can access http://localhost:3001/api
- [ ] All pages load correctly
- [ ] Voice assistant works
- [ ] Chatbot works

## 🆘 Getting Help

If you encounter issues:

1. **Check Common Problems:** See [Common Problems & Solutions](#common-problems--solutions) above
2. **Review Documentation:** Check other `.md` files in project
3. **Check Logs:** Look at terminal output for error messages
4. **Verify Setup:** Go through [Setup Verification Checklist](#-setup-verification-checklist)

## 📚 Additional Resources

- **Next.js Docs:** https://nextjs.org/docs
- **NestJS Docs:** https://docs.nestjs.com/
- **Vercel Docs:** https://vercel.com/docs
- **TypeScript Docs:** https://www.typescriptlang.org/docs/

---

**Setup Complete! Happy Coding! 🚀**

*Team: Anshika Singh, Nidhi Kumari, KumKum Kumari, Neha Kumari*
