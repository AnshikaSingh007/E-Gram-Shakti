# 🚀 E Gram Shakti - Digital Literacy Platform

## 👥 Team Members

- **Anshika Singh**
- **Nidhi Kumari**
- **KumKum Kumari**
- **Neha Kumari**

## 📋 Project Overview

Demo Video Link: https://youtu.be/Wi82__CXJx8?si=LQ3V2fEeeTr4mHpN
Drive Link:https://drive.google.com/drive/folders/1Pbkw3iPvGhM3NRmtxundSdGpCmCs17vM?usp=drive_link
Project Gallery : ![WhatsApp Image 2025-11-26 at 9 47 55 AM](https://github.com/user-attachments/assets/9c5d0f7c-df8e-4e54-b8c9-f3edebf88a61)


**E Gram Shakti** is an offline-first, voice-first, multilingual digital literacy platform designed for rural communities. It provides comprehensive digital education, government scheme information, healthcare services, market information, and digital payment capabilities.

## 🎯 Key Features

### ✅ Core Features
- **Voice Assistant** - Multilingual voice commands (Hindi/English)
- **Chatbot** - AI-powered chatbot with Gemini integration
- **Digital Lessons** - Interactive digital literacy lessons
- **Government Schemes** - Information about all government schemes
- **Healthcare Services** - Healthcare information and services
- **Market Information** - Real-time market prices and information
- **Digital Payments** - UPI and digital payment integration
- **Progress Tracking** - User progress and literacy score tracking
- **Offline Support** - Works completely offline with PWA
- **Multilingual** - Supports Hindi, English, and 8+ languages

### 🏗️ Technical Stack

**Frontend:**
- Next.js 16 (App Router)
- TypeScript
- React 19
- Tailwind CSS 4
- PWA (Service Worker)
- IndexedDB (localForage)

**Backend:**
- NestJS 11
- TypeScript
- REST API
- Supabase Integration
- Gemini AI Integration

**Infrastructure:**
- Vercel (Frontend Deployment)
- Railway/Render (Backend Deployment)
- Supabase (Database & Auth)

## 📁 Project Structure

```
Nidhi/
├── frontend/              # Next.js frontend application
│   ├── app/              # Next.js App Router pages
│   ├── components/       # React components
│   ├── lib/              # Utilities and API client
│   ├── public/           # Static assets
│   └── vercel.json       # Vercel deployment config
├── backend/              # NestJS backend application
│   ├── src/
│   │   ├── chatbot/      # Chatbot module
│   │   ├── ai/           # AI module
│   │   ├── lessons/      # Lessons module
│   │   ├── schemes/      # Government schemes
│   │   ├── healthcare/   # Healthcare services
│   │   ├── market/       # Market information
│   │   └── payments/     # Digital payments
│   └── package.json
├── docs/                 # Documentation
└── README.md            # This file
```

## 🚀 Quick Start

### Prerequisites
- Node.js 20+ installed
- npm or yarn
- Git

### Local Development Setup

#### 1. Clone Repository
```bash
git clone <repository-url>
cd Nidhi
```

#### 2. Install Dependencies

**Frontend:**
```bash
cd frontend
npm install
```

**Backend:**
```bash
cd backend
npm install
```

#### 3. Environment Variables

**Frontend** - Create `frontend/.env.local`:
```bash
NEXT_PUBLIC_API_URL=http://localhost:3001/api
NEXT_PUBLIC_SUPABASE_URL=your_supabase_url (optional)
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_key (optional)
```

**Backend** - Create `backend/.env`:
```bash
PORT=3001
GEMINI_API_KEY=your_gemini_api_key (optional)
SUPABASE_URL=your_supabase_url (optional)
SUPABASE_ANON_KEY=your_supabase_key (optional)
```

#### 4. Start Development Servers

**Terminal 1 - Backend:**
```bash
cd backend
npm run dev
```
Backend runs on: http://localhost:3001/api

**Terminal 2 - Frontend:**
```bash
cd frontend
npm run dev
```
Frontend runs on: http://localhost:3000

## 📚 Detailed Documentation

- **[SETUP_GUIDE.md](./SETUP_GUIDE.md)** - Complete setup instructions
- **[VERCEL_DEPLOYMENT.md](./VERCEL_DEPLOYMENT.md)** - Vercel deployment guide
- **[DEPLOY_TO_VERCEL.md](./DEPLOY_TO_VERCEL.md)** - Quick deployment steps
- **[PROJECT_STRUCTURE.md](./PROJECT_STRUCTURE.md)** - Detailed project structure
- **[API_ENDPOINTS.md](./docs/API_ENDPOINTS.md)** - API documentation

## 🔧 Common Problems & Solutions

### Problem 1: Backend Not Starting
**Error:** `Cannot read properties of undefined (reading 'get')`

**Solution:**
- Ensure all dependencies are installed: `cd backend && npm install`
- Check environment variables are set correctly
- Clear cache: `rm -rf node_modules/.cache .cache`
- Restart backend: `npm run dev`

### Problem 2: Frontend Build Fails
**Error:** `Type error` or `Build failed`

**Solution:**
- Check TypeScript errors: `npm run build`
- Ensure all dependencies installed: `npm install`
- Clear Next.js cache: `rm -rf .next`
- Rebuild: `npm run build`

### Problem 3: API Connection Failed
**Error:** `Failed to fetch` or `Network Error`

**Solution:**
- Verify backend is running on port 3001
- Check `NEXT_PUBLIC_API_URL` in frontend `.env.local`
- Ensure CORS is enabled on backend
- Test backend health: `curl http://localhost:3001/api/chatbot/health`

### Problem 4: Service Worker Not Working
**Error:** Service worker not registering

**Solution:**
- Ensure running in production mode or HTTPS
- Check `/sw.js` is accessible
- Verify headers in `next.config.ts`
- Clear browser cache and reload

### Problem 5: Port Already in Use
**Error:** `EADDRINUSE: address already in use :::3001`

**Solution:**
```bash
# Kill process on port 3001
lsof -ti:3001 | xargs kill -9

# Or use different port
PORT=3002 npm run dev
```

## 🌐 Deployment

### Frontend Deployment (Vercel)

1. **Install Vercel CLI:**
   ```bash
   npm install -g vercel
   ```

2. **Deploy:**
   ```bash
   cd frontend
   vercel
   ```

3. **Set Environment Variables in Vercel Dashboard:**
   - `NEXT_PUBLIC_API_URL` = Your backend URL

See [DEPLOY_TO_VERCEL.md](./DEPLOY_TO_VERCEL.md) for detailed steps.

### Backend Deployment

Deploy backend to:
- **Railway.app** (Recommended - Easiest)
- **Render.com**
- **Fly.io**
- Any Node.js hosting service

See [VERCEL_DEPLOYMENT.md](./VERCEL_DEPLOYMENT.md) for backend deployment options.

## 🧪 Testing

### Test Backend
```bash
# Health check
curl http://localhost:3001/api/chatbot/health

# Test chatbot
curl -X POST http://localhost:3001/api/chatbot/message \
  -H "Content-Type: application/json" \
  -d '{"message":"hello","language":"en"}'
```

### Test Frontend
1. Open http://localhost:3000
2. Navigate to all pages
3. Test voice assistant
4. Test chatbot
5. Test offline functionality

## 📱 Features in Detail

### Voice Assistant
- **Location:** `/voice`
- **Features:**
  - Multilingual voice recognition
  - Offline AI processing
  - Online AI integration
  - Auto language detection
  - Navigation commands

### Chatbot
- **Location:** `/chatbot`
- **Features:**
  - Gemini AI integration
  - Local intent detection (fallback)
  - Multilingual support
  - Quick action buttons
  - Auto-navigation

### Lessons
- **Location:** `/lessons`
- **Features:**
  - Digital literacy lessons
  - Progress tracking
  - Completion badges
  - Offline access

### Government Schemes
- **Location:** `/schemes`
- **Features:**
  - All government schemes
  - Filter by category
  - Detailed information
  - Application links

### Healthcare
- **Location:** `/healthcare`
- **Features:**
  - Healthcare services
  - Hospital information
  - Medicine information
  - Health tips

### Market Information
- **Location:** `/market`
- **Features:**
  - Real-time prices
  - Crop information
  - Market trends
  - Price alerts

### Digital Payments
- **Location:** `/payments`
- **Features:**
  - UPI integration
  - Transaction history
  - Payment methods
  - Security features

## 🔐 Security

- Environment variables for sensitive data
- CORS configuration
- Input validation
- Error handling
- Secure API endpoints

## 📊 Project Status

✅ **Frontend:** Complete and ready for deployment
✅ **Backend:** Complete and ready for deployment
✅ **PWA:** Fully functional
✅ **Offline Support:** Working
✅ **Voice Assistant:** Working
✅ **Chatbot:** Working
✅ **All Modules:** Implemented
✅ **Documentation:** Complete

## 🤝 Contributing

1. Fork the repository
2. Create feature branch: `git checkout -b feature-name`
3. Commit changes: `git commit -m 'Add feature'`
4. Push to branch: `git push origin feature-name`
5. Submit pull request

## 📝 License

This project is part of the E Gram Shakti initiative.

## 📞 Support

For issues and questions:
1. Check [Common Problems & Solutions](#-common-problems--solutions) above
2. Review documentation files
3. Check GitHub issues
4. Contact team members

## 🎉 Acknowledgments

- Team: Anshika Singh, Nidhi Kumari, KumKum Kumari, Neha Kumari
- Built with Next.js, NestJS, and modern web technologies
- Designed for rural digital literacy empowerment

---

**Made with ❤️ by Team E Gram Shakti**
