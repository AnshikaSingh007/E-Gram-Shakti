# 📁 Complete Project Structure

## Directory Tree

```
Nidhi/
│
├── 📁 backend/                    # NestJS Backend API
│   ├── src/
│   │   ├── analytics/            # Analytics module
│   │   │   ├── analytics.controller.ts
│   │   │   ├── analytics.service.ts
│   │   │   └── analytics.module.ts
│   │   │
│   │   ├── healthcare/           # Healthcare module
│   │   │   ├── healthcare.controller.ts
│   │   │   ├── healthcare.service.ts
│   │   │   ├── healthcare.module.ts
│   │   │   └── dto/
│   │   │
│   │   ├── lessons/              # Lessons module
│   │   │   ├── lessons.controller.ts
│   │   │   ├── lessons.service.ts
│   │   │   ├── lessons.module.ts
│   │   │   └── dto/
│   │   │
│   │   ├── market/               # Market module
│   │   │   ├── market.controller.ts
│   │   │   ├── market.service.ts
│   │   │   └── market.module.ts
│   │   │
│   │   ├── payments/             # Payments module
│   │   │   ├── payments.controller.ts
│   │   │   ├── payments.service.ts
│   │   │   └── payments.module.ts
│   │   │
│   │   ├── schemes/              # Schemes module
│   │   │   ├── schemes.controller.ts
│   │   │   ├── schemes.service.ts
│   │   │   ├── schemes.module.ts
│   │   │   └── dto/
│   │   │
│   │   ├── tests/                # Tests module
│   │   │   ├── tests.controller.ts
│   │   │   ├── tests.service.ts
│   │   │   └── tests.module.ts
│   │   │
│   │   ├── users/                # Users module
│   │   │   ├── users.controller.ts
│   │   │   ├── users.service.ts
│   │   │   └── users.module.ts
│   │   │
│   │   ├── seed/                 # Database seeding
│   │   │   ├── seed.service.ts
│   │   │   └── seed.module.ts
│   │   │
│   │   ├── supabase/             # Database service
│   │   │   ├── supabase.service.ts
│   │   │   └── supabase.module.ts
│   │   │
│   │   ├── app.module.ts         # Root module
│   │   ├── app.controller.ts     # Root controller
│   │   ├── app.service.ts        # Root service
│   │   └── main.ts               # Entry point
│   │
│   ├── package.json
│   ├── tsconfig.json
│   └── .env                      # Environment variables
│
├── 📁 frontend/                   # Next.js Frontend (PWA)
│   ├── app/                      # App Router
│   │   ├── admin/                # Admin panel
│   │   │   └── page.tsx
│   │   │
│   │   ├── dashboard/            # Analytics dashboard
│   │   │   └── page.tsx
│   │   │
│   │   ├── healthcare/           # Healthcare page
│   │   │   └── page.tsx
│   │   │
│   │   ├── lessons/              # Lessons page
│   │   │   └── page.tsx
│   │   │
│   │   ├── market/               # Market page
│   │   │   └── page.tsx
│   │   │
│   │   ├── payments/             # Payments page
│   │   │   └── page.tsx
│   │   │
│   │   ├── schemes/              # Schemes page
│   │   │   └── page.tsx
│   │   │
│   │   ├── services/             # All services
│   │   │   └── page.tsx
│   │   │
│   │   ├── voice/                # Voice assistant
│   │   │   └── page.tsx
│   │   │
│   │   ├── card/                 # Digital card
│   │   │   └── page.tsx
│   │   │
│   │   ├── progress/             # User progress
│   │   │   └── page.tsx
│   │   │
│   │   ├── test/                 # Literacy test
│   │   │   └── page.tsx
│   │   │
│   │   ├── layout.tsx            # Root layout
│   │   ├── page.tsx              # Home page
│   │   └── globals.css           # Global styles
│   │
│   ├── components/               # React components
│   │   ├── Navigation.tsx        # Main navigation
│   │   ├── PageLayout.tsx        # Page wrapper
│   │   └── ...
│   │
│   ├── lib/                      # Utilities
│   │   ├── api.ts                # API client
│   │   ├── storage.ts            # Local storage
│   │   ├── i18n.ts               # Translations
│   │   └── ...
│   │
│   ├── hooks/                    # Custom hooks
│   │   ├── useLanguage.ts        # Language hook
│   │   └── ...
│   │
│   ├── public/                   # Static assets
│   ├── package.json
│   ├── next.config.ts
│   └── tailwind.config.ts
│
├── 📄 README.md                  # Main documentation
├── 📄 QUICK_START.md             # Quick start guide
├── 📄 SETUP_GUIDE.md             # Detailed setup
├── 📄 PROJECT_STRUCTURE.md       # This file
└── 📄 package.json               # Root package (optional)
```

## Backend Modules

### Core Modules
- **Analytics** - Statistics and analytics
- **Users** - User management
- **Lessons** - Digital literacy lessons
- **Schemes** - Government schemes
- **Tests** - Literacy assessments

### Feature Modules
- **Healthcare** - Health services & records
- **Market** - Market prices & agricultural tips
- **Payments** - Digital payment methods

### Support Modules
- **Seed** - Database seeding service
- **Supabase** - Database connection service

## Frontend Pages

### Main Pages
- `/` - Home page
- `/admin` - Admin panel
- `/dashboard` - Analytics dashboard
- `/services` - All services overview

### Feature Pages
- `/lessons` - Digital lessons
- `/schemes` - Government schemes
- `/healthcare` - Healthcare services
- `/market` - Market information
- `/payments` - Payment methods

### User Pages
- `/card` - Digital identity card
- `/progress` - Learning progress
- `/test` - Literacy test
- `/voice` - Voice assistant

## Key Configuration Files

### Backend
- `backend/src/main.ts` - Server configuration
- `backend/src/app.module.ts` - Module imports
- `backend/package.json` - Dependencies

### Frontend
- `frontend/app/layout.tsx` - Root layout
- `frontend/lib/api.ts` - API configuration
- `frontend/next.config.ts` - Next.js config
- `frontend/package.json` - Dependencies

## API Structure

```
/api
├── /analytics
│   ├── GET /summary
│   ├── GET /villages
│   └── GET /literacy-distribution
│
├── /lessons
│   ├── GET /
│   ├── GET /:id
│   └── POST /:id/complete
│
├── /schemes
│   ├── GET /
│   └── GET /:id
│
├── /healthcare
│   ├── GET /services
│   ├── GET /records/:userId
│   └── POST /records
│
├── /market
│   ├── GET /prices
│   └── GET /tips
│
└── /payments
    ├── GET /methods/:userId
    └── GET /transactions/:userId
```

## Data Flow

```
Frontend (Next.js)
    ↓ API Calls
lib/api.ts
    ↓ HTTP Requests
Backend (NestJS)
    ↓ Business Logic
Services
    ↓ Data Access
Supabase (Optional) / Sample Data
```

## Environment Variables

### Backend (.env)
```env
PORT=3001
FRONTEND_URL=http://localhost:3000
SUPABASE_URL=optional
SUPABASE_ANON_KEY=optional
```

### Frontend (.env.local)
```env
NEXT_PUBLIC_API_URL=http://localhost:3001/api
```

---

**This structure supports:**
- ✅ Modular architecture
- ✅ Scalable codebase
- ✅ Easy maintenance
- ✅ Feature additions

