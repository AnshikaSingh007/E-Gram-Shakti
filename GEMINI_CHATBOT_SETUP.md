# 🤖 Gemini AI Chatbot Integration - Setup Guide

## Overview

The chatbot has been integrated with Google's Gemini AI API for intelligent, context-aware responses. The system works with or without Gemini API key, falling back to local intent detection.

## ✅ Implementation Complete

### 1. **Backend Integration** (`backend/src/chatbot/chatbot.service.ts`)
- Gemini API integration
- Fallback to local intent detection
- Multilingual support (Hindi/English)
- Navigation intent extraction
- Error handling

### 2. **Frontend Chatbot Page** (`frontend/app/chatbot/page.tsx`)
- Beautiful chat interface
- Real-time messaging
- Quick action buttons
- Online/offline indicators
- Multilingual support

### 3. **Navigation Integration**
- Added chatbot link to navigation
- Added to home page features
- i18n translations added

## 🔑 Setup Instructions

### Step 1: Get Gemini API Key

1. Go to [Google AI Studio](https://makersuite.google.com/app/apikey)
2. Sign in with your Google account
3. Click "Create API Key"
4. Copy your API key

### Step 2: Configure Backend

1. Create or update `.env` file in `backend/` directory:

```bash
# Backend .env file
GEMINI_API_KEY=your_gemini_api_key_here
```

2. The backend will automatically use the API key if provided.

### Step 3: Test the Integration

1. Start the backend:
```bash
cd backend
npm run dev
```

2. Start the frontend:
```bash
cd frontend
npm run dev
```

3. Navigate to `/chatbot` page
4. Try asking questions in Hindi or English

## 🎯 Features

### With Gemini API Key
- **Intelligent Responses**: Context-aware answers using Gemini Pro
- **Natural Language**: Understands complex queries
- **Multilingual**: Works in Hindi and English
- **Navigation**: Automatically detects navigation intents

### Without Gemini API Key
- **Local Intent Detection**: Falls back to keyword-based detection
- **Navigation Support**: Still provides navigation commands
- **Multilingual**: Works in Hindi and English
- **Offline Support**: Works completely offline

## 💬 Usage Examples

### Hindi Queries
- "डिजिटल साक्षरता क्या है?"
- "सरकारी योजनाओं के बारे में बताएं"
- "UPI कैसे काम करता है?"
- "सबक खोलें"

### English Queries
- "What is digital literacy?"
- "Tell me about government schemes"
- "How does UPI work?"
- "Open lessons"

## 🔄 Processing Flow

```
User sends message
  ↓
Check if Gemini API key exists
  ↓
If yes: Call Gemini API
  ├─ Success: Return intelligent response
  └─ Error: Fall back to local detection
  ↓
If no: Use local intent detection
  ↓
Extract navigation intents
  ↓
Return response with action (if applicable)
  ↓
Frontend displays response
  ↓
Auto-navigate if action provided
```

## 📝 API Configuration

### Gemini API Endpoint
```
https://generativelanguage.googleapis.com/v1beta/models/gemini-pro:generateContent
```

### Request Format
```json
{
  "contents": [{
    "parts": [{
      "text": "System prompt + User message"
    }]
  }],
  "generationConfig": {
    "temperature": 0.7,
    "topK": 40,
    "topP": 0.95,
    "maxOutputTokens": 500
  }
}
```

## 🛠️ Troubleshooting

### Issue: Chatbot not responding
- **Check**: Backend is running on port 3001
- **Check**: API key is set in `.env` file
- **Check**: Network connectivity

### Issue: Gemini API errors
- **Check**: API key is valid
- **Check**: API quota not exceeded
- **Solution**: System automatically falls back to local detection

### Issue: Navigation not working
- **Check**: Response includes `action: 'navigate'`
- **Check**: `data.url` is provided
- **Check**: Frontend is handling navigation correctly

## 📊 Status

✅ **Backend**: Gemini integration complete
✅ **Frontend**: Chatbot page created
✅ **Navigation**: Integrated in menu
✅ **Multilingual**: Hindi/English support
✅ **Error Handling**: Graceful fallbacks
✅ **Offline Support**: Works without API key

## 🚀 Next Steps

1. Add your Gemini API key to `.env`
2. Test the chatbot with various queries
3. Customize system prompts for better responses
4. Add more language support if needed

---

**Gemini Chatbot Integration Complete!** 🎉

The chatbot now provides intelligent, AI-powered responses while maintaining offline functionality.

