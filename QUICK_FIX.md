# 🔧 Quick Fix - Backend Not Running

## Problem
Backend server (port 3001) is not responding.

## Solution

### Step 1: Kill All Old Processes
```bash
pkill -9 -f "tsx.*backend"
pkill -9 -f "node.*backend"
```

### Step 2: Start Backend Fresh
```bash
cd /Users/akashsingh/Downloads/Nidhi/backend
npm run dev
```

**Wait for this message:**
```
Backend server running on http://localhost:3001/api
```

### Step 3: Verify
Open a new terminal and run:
```bash
curl http://localhost:3001/api/chatbot/health
```

Should return:
```json
{"status":"ok","service":"chatbot","timestamp":"..."}
```

## If Still Not Working

### Check Dependencies
```bash
cd backend
npm install
```

### Check for Errors
Look at the terminal output when running `npm run dev` for any error messages.

### Manual Start
```bash
cd backend
npx tsx src/main.ts
```

## Common Issues

1. **Port 3001 in use**: `lsof -ti:3001 | xargs kill -9`
2. **Missing dependencies**: `npm install`
3. **TypeScript errors**: Check `src/` files for syntax errors
4. **Module errors**: Check `src/app.module.ts` imports

## Success Indicators

✅ Terminal shows: "Backend server running on http://localhost:3001/api"
✅ `curl http://localhost:3001/api/chatbot/health` returns JSON
✅ Frontend can connect to backend

