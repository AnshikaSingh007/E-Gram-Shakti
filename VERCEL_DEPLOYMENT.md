# 🚀 Vercel Deployment Guide - Complete Setup

## 👥 Team Members

- **Anshika Singh**
- **Nidhi Kumari**
- **KumKum Kumari**
- **Neha Kumari**

## ✅ Project Analysis Complete

The project has been analyzed and configured for Vercel deployment. All necessary files and configurations have been created.

## 📋 Pre-Deployment Checklist

### ✅ Completed
- [x] Vercel configuration file created (`vercel.json`)
- [x] Next.js config optimized for Vercel
- [x] Environment variables documented
- [x] Build configuration verified
- [x] API URL configuration updated
- [x] Service worker compatibility checked
- [x] PWA manifest configured

## 🎯 Deployment Steps

### Step 1: Prepare Repository

1. **Ensure all changes are committed:**
   ```bash
   git add .
   git commit -m "Prepare for Vercel deployment"
   git push
   ```

### Step 2: Deploy to Vercel

#### Option A: Via Vercel Dashboard (Recommended)

1. Go to [vercel.com](https://vercel.com)
2. Sign in with GitHub/GitLab/Bitbucket
3. Click "Add New Project"
4. Import your repository
5. Configure project:
   - **Framework Preset:** Next.js
   - **Root Directory:** `frontend`
   - **Build Command:** `npm run build` (auto-detected)
   - **Output Directory:** `.next` (auto-detected)
   - **Install Command:** `npm install` (auto-detected)

#### Option B: Via Vercel CLI

```bash
# Install Vercel CLI
npm i -g vercel

# Login
vercel login

# Deploy
cd frontend
vercel

# Follow prompts:
# - Set up and deploy? Yes
# - Which scope? Your account
# - Link to existing project? No (first time) or Yes (updates)
# - What's your project's name? e-gram-shakti
# - In which directory is your code located? ./
```

### Step 3: Configure Environment Variables

In Vercel Dashboard → Project → Settings → Environment Variables:

#### Required Variables:
```
NEXT_PUBLIC_API_URL=https://your-backend-url.com/api
```

#### Optional Variables:
```
NEXT_PUBLIC_SUPABASE_URL=your_supabase_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_key
```

**Important:** 
- Replace `your-backend-url.com` with your actual backend URL
- Backend needs to be deployed separately (see Backend Deployment section)

### Step 4: Deploy Backend

The backend (NestJS) needs to be deployed separately. Options:

#### Option A: Deploy Backend to Railway/Render/Fly.io
1. Deploy backend to a service like Railway, Render, or Fly.io
2. Get the backend URL
3. Set `NEXT_PUBLIC_API_URL` in Vercel to point to backend URL

#### Option B: Use Vercel Serverless Functions (Advanced)
- Convert backend API routes to Vercel serverless functions
- More complex but keeps everything in one place

#### Option C: Use Backend as Separate Service
- Deploy backend to a VPS, AWS, or other hosting
- Update `NEXT_PUBLIC_API_URL` in Vercel

### Step 5: Verify Deployment

1. **Check Build Logs:**
   - Vercel Dashboard → Deployments → View build logs
   - Ensure build completes successfully

2. **Test Live Site:**
   - Visit your Vercel URL (e.g., `your-project.vercel.app`)
   - Test all pages
   - Test API connections

3. **Check Environment Variables:**
   - Verify all env vars are set correctly
   - Test API calls work

## 🔧 Configuration Files Created

### 1. `frontend/vercel.json`
- Framework detection
- Build configuration
- Service worker rewrites
- Headers for PWA

### 2. `frontend/.vercelignore`
- Excludes unnecessary files from deployment

### 3. `frontend/.env.example`
- Template for environment variables

### 4. Updated `next.config.ts`
- Removed standalone output (Vercel handles this)
- Added proper headers
- Optimized for production

## 🌐 Environment Variables

### Production Setup

In Vercel Dashboard, set these environment variables:

```bash
# Required
NEXT_PUBLIC_API_URL=https://your-backend-api.com/api

# Optional (if using Supabase)
NEXT_PUBLIC_SUPABASE_URL=https://your-project.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_anon_key
```

### Local Development

Create `frontend/.env.local`:
```bash
NEXT_PUBLIC_API_URL=http://localhost:3001/api
NEXT_PUBLIC_SUPABASE_URL=your_local_supabase_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_local_key
```

## 🏗️ Project Structure for Vercel

```
frontend/              # Vercel deployment root
├── app/               # Next.js App Router
├── components/        # React components
├── lib/               # Utilities and API client
├── public/            # Static assets
├── vercel.json        # Vercel configuration
├── next.config.ts     # Next.js configuration
└── package.json       # Dependencies
```

## ⚠️ Important Notes

### Backend Deployment
- **Backend must be deployed separately** - Vercel is for frontend
- Backend URL must be accessible from the internet
- CORS must be configured on backend to allow Vercel domain

### API Configuration
- Frontend uses `NEXT_PUBLIC_API_URL` environment variable
- Falls back to `localhost:3001` in development
- Must be set in Vercel for production

### Service Worker
- Service worker works on Vercel
- PWA features are supported
- Offline functionality works

### Build Optimization
- Next.js automatically optimizes for Vercel
- Static pages are pre-rendered
- Dynamic pages use serverless functions

## 🐛 Troubleshooting

### Build Fails
1. Check build logs in Vercel dashboard
2. Ensure all dependencies are in `package.json`
3. Verify TypeScript compilation passes
4. Check for missing environment variables

### API Not Working
1. Verify `NEXT_PUBLIC_API_URL` is set correctly
2. Check backend is deployed and accessible
3. Verify CORS settings on backend
4. Check browser console for errors

### Service Worker Issues
1. Ensure `/sw.js` is accessible
2. Check `vercel.json` rewrites
3. Verify headers are set correctly

## 📊 Deployment Status

✅ **Frontend:** Ready for Vercel deployment
✅ **Configuration:** All files created
✅ **Build:** Verified working
✅ **Environment Variables:** Documented
⚠️ **Backend:** Needs separate deployment

## 🚀 Quick Deploy

```bash
# 1. Install Vercel CLI
npm i -g vercel

# 2. Navigate to frontend
cd frontend

# 3. Deploy
vercel

# 4. Set environment variables in Vercel dashboard
# 5. Redeploy if needed
vercel --prod
```

## 📝 Post-Deployment

1. **Set Custom Domain** (Optional)
   - Vercel Dashboard → Settings → Domains
   - Add your custom domain

2. **Enable Analytics** (Optional)
   - Vercel Dashboard → Analytics
   - Enable for insights

3. **Set Up Monitoring**
   - Check deployment logs
   - Monitor API calls
   - Test all features

## 🎉 Success Indicators

✅ Build completes without errors
✅ Site loads on Vercel URL
✅ All pages accessible
✅ API calls work (if backend deployed)
✅ PWA features work
✅ Service worker registers

---

**Ready for Vercel Deployment!** 🚀

Follow the steps above to deploy your frontend to Vercel.

