# 👥 Team Guide - E Gram Shakti

## Team Members

- **Anshika Singh**
- **Nidhi Kumari**
- **KumKum Kumari**
- **Neha Kumari**

## 📋 Quick Reference

### For New Team Members

1. **Read First:**
   - [README.md](./README.md) - Project overview
   - [SETUP_GUIDE.md](./SETUP_GUIDE.md) - Setup instructions
   - [PROBLEMS_AND_SOLUTIONS.md](./PROBLEMS_AND_SOLUTIONS.md) - Common issues

2. **Setup Your Environment:**
   ```bash
   # Clone repository
   git clone <repo-url>
   cd Nidhi
   
   # Install dependencies
   cd frontend && npm install
   cd ../backend && npm install
   
   # Create environment files
   # See SETUP_GUIDE.md for details
   ```

3. **Start Development:**
   ```bash
   # Terminal 1: Backend
   cd backend && npm run dev
   
   # Terminal 2: Frontend
   cd frontend && npm run dev
   ```

## 🎯 Project Structure Overview

```
Nidhi/
├── frontend/          # Next.js frontend (Port 3000)
│   ├── app/          # Pages and routes
│   ├── components/   # React components
│   └── lib/          # Utilities
├── backend/          # NestJS backend (Port 3001)
│   └── src/          # Backend modules
└── docs/             # Documentation
```

## 🔑 Key Files to Know

### Frontend
- `frontend/app/page.tsx` - Home page
- `frontend/lib/api.ts` - API client
- `frontend/components/Navigation.tsx` - Main navigation
- `frontend/next.config.ts` - Next.js configuration

### Backend
- `backend/src/main.ts` - Backend entry point
- `backend/src/app.module.ts` - Main module
- `backend/src/chatbot/` - Chatbot module
- `backend/src/ai/` - AI module

## 🚀 Common Tasks

### Adding a New Page

1. **Create page file:**
   ```bash
   frontend/app/new-page/page.tsx
   ```

2. **Add to navigation:**
   ```typescript
   // frontend/components/Navigation.tsx
   { href: '/new-page', label: 'New Page', labelKey: 'newPage', icon: '📄' }
   ```

3. **Add translations:**
   ```typescript
   // frontend/lib/i18n.ts
   newPage: 'New Page',
   ```

### Adding a New API Endpoint

1. **Create service:**
   ```typescript
   // backend/src/new-module/new-module.service.ts
   @Injectable()
   export class NewModuleService {
     // Your service logic
   }
   ```

2. **Create controller:**
   ```typescript
   // backend/src/new-module/new-module.controller.ts
   @Controller('new-module')
   export class NewModuleController {
     @Get()
     findAll() {
       return this.service.findAll();
     }
   }
   ```

3. **Register in module:**
   ```typescript
   // backend/src/new-module/new-module.module.ts
   @Module({
     controllers: [NewModuleController],
     providers: [NewModuleService],
   })
   ```

### Testing Changes

1. **Test Backend:**
   ```bash
   curl http://localhost:3001/api/your-endpoint
   ```

2. **Test Frontend:**
   - Open http://localhost:3000
   - Navigate to your page
   - Check browser console

3. **Test Build:**
   ```bash
   cd frontend && npm run build
   cd ../backend && npm run build
   ```

## 🐛 When Things Go Wrong

### Backend Not Starting
1. Check if port 3001 is free
2. Verify `.env` file exists
3. Check `npm install` completed
4. See [PROBLEMS_AND_SOLUTIONS.md](./PROBLEMS_AND_SOLUTIONS.md)

### Frontend Not Working
1. Check if backend is running
2. Verify `.env.local` file
3. Clear `.next` cache: `rm -rf .next`
4. See [PROBLEMS_AND_SOLUTIONS.md](./PROBLEMS_AND_SOLUTIONS.md)

### API Errors
1. Check backend is running
2. Verify `NEXT_PUBLIC_API_URL` in frontend
3. Check CORS settings
4. Test endpoint directly with curl

## 📝 Code Standards

### TypeScript
- Use TypeScript for all new code
- Define proper interfaces
- Avoid `any` when possible

### React Components
- Use functional components
- Use hooks for state
- Keep components small and focused

### API Design
- Use RESTful conventions
- Return consistent JSON
- Handle errors properly

## 🔄 Git Workflow

1. **Create branch:**
   ```bash
   git checkout -b feature/your-feature-name
   ```

2. **Make changes and commit:**
   ```bash
   git add .
   git commit -m "Add: Description of changes"
   ```

3. **Push and create PR:**
   ```bash
   git push origin feature/your-feature-name
   ```

## 📚 Documentation Standards

- Update README.md for major changes
- Document new features
- Add comments to complex code
- Update this guide if needed

## 🎓 Learning Resources

- **Next.js:** https://nextjs.org/docs
- **NestJS:** https://docs.nestjs.com/
- **TypeScript:** https://www.typescriptlang.org/docs/
- **React:** https://react.dev/

## ✅ Daily Checklist

- [ ] Pull latest changes: `git pull`
- [ ] Check if backend is running
- [ ] Check if frontend is running
- [ ] Test your changes
- [ ] Commit and push changes

## 🆘 Getting Help

1. Check [PROBLEMS_AND_SOLUTIONS.md](./PROBLEMS_AND_SOLUTIONS.md)
2. Review documentation files
3. Check GitHub issues
4. Ask team members

---

**Welcome to the Team! Happy Coding! 🚀**

*Team: Anshika Singh, Nidhi Kumari, KumKum Kumari, Neha Kumari*

