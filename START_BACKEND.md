# 🚀 Start Backend Server

## Quick Start

```bash
# Navigate to backend directory
cd backend

# Install dependencies (if not already installed)
npm install

# Start the backend server
npm run dev
```

The backend will start on **http://localhost:3001**

## Verify Backend is Running

Open a new terminal and run:
```bash
curl http://localhost:3001/api/chatbot/health
```

You should see:
```json
{
  "status": "ok",
  "service": "chatbot",
  "timestamp": "..."
}
```

## Environment Variables (Optional)

Create a `.env` file in the `backend/` directory:

```bash
# Gemini AI API Key (Optional - for enhanced chatbot)
GEMINI_API_KEY=your_gemini_api_key_here

# Supabase (Optional)
SUPABASE_URL=your_supabase_url
SUPABASE_ANON_KEY=your_supabase_key

# Server Port (Default: 3001)
PORT=3001
```

## Troubleshooting

### Port 3001 Already in Use
```bash
# Kill process on port 3001
lsof -ti:3001 | xargs kill -9

# Then restart
npm run dev
```

### Backend Not Starting
1. Check Node.js version: `node --version` (should be 18+)
2. Install dependencies: `npm install`
3. Check for errors in terminal output

### Chatbot Not Working
- Backend works without Gemini API key (uses local detection)
- Add `GEMINI_API_KEY` to `.env` for AI-powered responses
- Get key from: https://makersuite.google.com/app/apikey

