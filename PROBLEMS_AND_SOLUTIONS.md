# 🔧 Problems & Solutions Guide

## 👥 Team Members

- **Anshika Singh**
- **Nidhi Kumari**
- **KumKum Kumari**
- **Neha Kumari**

## 📋 Overview

This document explains all the problems encountered during development and their solutions. This will help team members and future developers understand issues and fix them quickly.

## 🐛 Common Problems & Solutions

### Problem 1: Backend Dependency Injection Error

**Error Message:**
```
TypeError: Cannot read properties of undefined (reading 'get')
at new ChatbotService
```

**Problem Explanation:**
- NestJS dependency injection failed
- ConfigService was not properly injected
- Service tried to access ConfigService before it was available

**Solution Applied:**
1. Removed ConfigService dependency from ChatbotService
2. Used `process.env` directly for environment variables
3. Made service work without external dependencies

**Code Fix:**
```typescript
// Before (Problematic)
constructor(private configService: ConfigService) {
  this.geminiApiKey = this.configService.get<string>('GEMINI_API_KEY');
}

// After (Fixed)
constructor() {
  this.geminiApiKey = process.env.GEMINI_API_KEY || '';
}
```

**Prevention:**
- Always check if dependencies are properly injected
- Use optional dependencies with fallbacks
- Test service initialization

---

### Problem 2: Frontend Build Configuration Error

**Error Message:**
```
Type error: Object literal may only specify known properties, and 'swcMinify' does not exist in type 'NextConfig'
```

**Problem Explanation:**
- Next.js 16 removed `swcMinify` option (SWC is default)
- `compress` option is also not needed
- Configuration was using outdated options

**Solution Applied:**
1. Removed `swcMinify` option
2. Removed `compress` option
3. Kept only valid Next.js 16 options

**Code Fix:**
```typescript
// Before (Problematic)
const nextConfig: NextConfig = {
  swcMinify: true,  // ❌ Not valid in Next.js 16
  compress: true,    // ❌ Not valid
};

// After (Fixed)
const nextConfig: NextConfig = {
  reactStrictMode: true,
  // SWC is default, no need to specify
  // Compression is automatic
};
```

**Prevention:**
- Check Next.js version compatibility
- Review Next.js documentation for valid options
- Test build after configuration changes

---

### Problem 3: API Connection Failed

**Error Message:**
```
Failed to fetch
TypeError: Failed to fetch
Network Error
```

**Problem Explanation:**
- Frontend couldn't connect to backend
- Backend was not running
- CORS issues
- Wrong API URL

**Solution Applied:**
1. Added timeout handling (5 seconds)
2. Added network error detection
3. Implemented graceful fallback to local storage
4. Improved error messages

**Code Fix:**
```typescript
// Added timeout and error handling
const controller = new AbortController();
const timeoutId = setTimeout(() => controller.abort(), 5000);

try {
  const response = await fetch(url, {
    ...options,
    signal: controller.signal,
  });
  // Handle response
} catch (error) {
  // Graceful fallback
  if (error.name === 'AbortError' || error.message?.includes('fetch')) {
    throw new Error('NETWORK_ERROR'); // Allow fallback
  }
}
```

**Prevention:**
- Always check backend is running
- Verify environment variables
- Test API endpoints separately
- Implement proper error handling

---

### Problem 4: Port Already in Use

**Error Message:**
```
Error: listen EADDRINUSE: address already in use :::3001
```

**Problem Explanation:**
- Previous backend process still running
- Port 3001 was occupied
- Multiple instances started

**Solution Applied:**
1. Kill existing processes on port
2. Clear process cache
3. Restart cleanly

**Commands:**
```bash
# Kill process on port 3001
lsof -ti:3001 | xargs kill -9

# Or use different port
PORT=3002 npm run dev
```

**Prevention:**
- Always stop previous instances
- Check port availability before starting
- Use process managers (PM2) for production

---

### Problem 5: Service Worker Not Registering

**Error Message:**
```
Service Worker registration failed
```

**Problem Explanation:**
- Service workers need HTTPS or localhost
- File not accessible
- Headers not configured correctly

**Solution Applied:**
1. Added proper headers in `next.config.ts`
2. Configured rewrites in `vercel.json`
3. Ensured file is in public directory
4. Added proper cache headers

**Code Fix:**
```typescript
// next.config.ts
async headers() {
  return [
    {
      source: '/sw.js',
      headers: [
        {
          key: 'Service-Worker-Allowed',
          value: '/',
        },
        {
          key: 'Cache-Control',
          value: 'public, max-age=0, must-revalidate',
        },
      ],
    },
  ];
}
```

**Prevention:**
- Test service worker in production build
- Verify headers are set correctly
- Check browser console for errors

---

### Problem 6: Hydration Mismatch Error

**Error Message:**
```
Hydration failed because the initial UI does not match what was rendered on the server
```

**Problem Explanation:**
- Server and client rendered different content
- Dynamic IDs generated differently
- Date/time differences

**Solution Applied:**
1. Added `suppressHydrationWarning` to html/body
2. Used consistent ID generation
3. Made dynamic content client-only

**Code Fix:**
```typescript
// layout.tsx
<html lang="hi" suppressHydrationWarning>
  <body suppressHydrationWarning>
    {children}
  </body>
</html>

// Use consistent IDs
const id = Math.random().toString(36).substring(2, 9);
// Instead of: Date.now()
```

**Prevention:**
- Avoid server/client mismatches
- Use consistent ID generation
- Test hydration in development

---

### Problem 7: TypeScript Type Errors

**Error Message:**
```
Type error: Property 'xxx' does not exist on type 'unknown'
```

**Problem Explanation:**
- API responses typed as `unknown`
- Missing type definitions
- Type assertions needed

**Solution Applied:**
1. Added type assertions where needed
2. Created proper interfaces
3. Used `as any` for dynamic responses

**Code Fix:**
```typescript
// Before
const response = await api.getData();
const id = response.id; // ❌ Error

// After
const response = await api.getData();
const id = (response as any).id; // ✅ Works
```

**Prevention:**
- Define proper TypeScript interfaces
- Use type guards
- Add type assertions carefully

---

### Problem 8: Vercel Deployment Build Error

**Error Message:**
```
Build failed
Invalid next.config.ts options
```

**Problem Explanation:**
- Invalid Next.js configuration
- Outdated options
- Type mismatches

**Solution Applied:**
1. Removed invalid options
2. Updated to Next.js 16 compatible config
3. Removed `standalone` output (Vercel handles this)

**Code Fix:**
```typescript
// Removed for Vercel
// output: 'standalone', // Vercel handles this automatically

// Removed invalid options
// swcMinify: true, // Default in Next.js 16
// compress: true, // Automatic
```

**Prevention:**
- Test build locally before deploying
- Check Next.js version compatibility
- Review Vercel documentation

---

### Problem 9: Missing Environment Variables

**Error Message:**
```
undefined
API calls failing
```

**Problem Explanation:**
- Environment variables not set
- Wrong variable names
- Not accessible in browser

**Solution Applied:**
1. Used `NEXT_PUBLIC_` prefix for client variables
2. Created `.env.example` file
3. Documented all required variables

**Solution:**
```bash
# Frontend .env.local
NEXT_PUBLIC_API_URL=http://localhost:3001/api

# Backend .env
PORT=3001
GEMINI_API_KEY=your_key_here
```

**Prevention:**
- Always use `NEXT_PUBLIC_` for client variables
- Document all environment variables
- Provide `.env.example` file

---

### Problem 10: Card Section Removal Issues

**Error Message:**
```
Cannot find module './card'
Reference to deleted page
```

**Problem Explanation:**
- Card page was deleted
- References still existed
- Navigation links broken

**Solution Applied:**
1. Removed all card references
2. Updated navigation
3. Removed from services page
4. Cleaned up storage references

**Prevention:**
- Search for all references before deleting
- Update navigation after page removal
- Test all links after changes

---

## 🎯 Best Practices to Avoid Problems

### 1. Always Test Locally First
```bash
# Test build before deploying
npm run build

# Test production build
npm run build && npm start
```

### 2. Check Dependencies
```bash
# Verify all dependencies installed
npm install

# Check for outdated packages
npm outdated
```

### 3. Environment Variables
- Always use `.env.example` as template
- Document all required variables
- Use `NEXT_PUBLIC_` for client variables

### 4. Error Handling
- Always implement try-catch
- Provide fallback mechanisms
- Log errors for debugging

### 5. Type Safety
- Define proper TypeScript interfaces
- Use type assertions carefully
- Enable strict mode

### 6. Testing
- Test all features after changes
- Verify API connections
- Check offline functionality

---

## 📚 Additional Resources

- **NestJS Error Handling:** https://docs.nestjs.com/exception-filters
- **Next.js Troubleshooting:** https://nextjs.org/docs/app/building-your-application/configuring/debugging
- **TypeScript Errors:** https://www.typescriptlang.org/docs/handbook/error.html

---

**Remember:** Most problems have simple solutions. Always check:
1. Dependencies installed?
2. Environment variables set?
3. Servers running?
4. Ports available?
5. Configuration correct?

*Team: Anshika Singh, Nidhi Kumari, KumKum Kumari, Neha Kumari*

