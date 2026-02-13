# Semih's Golden Tech Stack Template
> The ultimate, opinionated Next.js stack optimized for speed and DX.

## 🛠️ Core Technologies
*   **Framework:** Next.js 15+ (App Router)
*   **Language:** TypeScript 5.7+
*   **Styling:** Tailwind CSS v4 + Shadcn UI
*   **Database:** Supabase (Auth + DB + Realtime)
*   **State Management:** Zustand
*   **Forms:** React Hook Form + Zod
*   **Icons:** Lucide React

## 📦 File Structure
```
src/
├── app/
│   ├── (auth)/             # Login/Register pages
│   ├── (dashboard)/        # Main app pages
│   ├── api/                # API Routes
│   ├── layout.tsx          # Root Layout
│   └── globals.css         # Tailwind directives
├── components/
│   ├── ui/                 # Shadcn UI primitives (Button, Card...)
│   ├── shared/             # Reusable custom components
│   └── layout/             # Header, Sidebar, Footer
├── lib/
│   ├── supabase/           # Supabase client & server utils
│   ├── store/              # Zustand stores
│   ├── utils.ts            # CN helper for Tailwind
│   └── types.ts            # Global TS types
└── actions/                # Server Actions (No API needed!)
```

## 🚀 Initialization Commands

### 1. Create Next.js App
```bash
npx create-next-app@latest my-app --typescript --tailwind --eslint
```

### 2. Install Shadcn UI
```bash
npx shadcn-ui@latest init
# Creating components.json...
# Style: New York
# Base Color: Zinc
# CSS Variables: Yes
```

### 3. Install Core Dependencies
```bash
npm install @supabase/ssr @supabase/supabase-js zustand lucide-react clsx tailwind-merge react-hook-form @hookform/resolvers zod
```

### 4. Setup Supabase Client (`lib/supabase/client.ts`)
```typescript
import { createBrowserClient } from '@supabase/ssr'

export function createClient() {
  return createBrowserClient(
    process.env.NEXT_PUBLIC_SUPABASE_URL!,
    process.env.NEXT_PUBLIC_SUPABASE_ANON_KEY!
  )
}
```

## 🎨 Theme Config (Tailwind v4)
*   **Primary Color:** Zinc/Slate (Professional look)
*   **Fonts:** Inter (Sans), JetBrains Mono (Code)
*   **Animation:** `animate-in` utilities from Shadcn

## 🛡️ Security Rules
1.  **RLS (Row Level Security):** Enable on Supabase tables immediately.
2.  **Environment Variables:** Store secrets in `.env.local` and never commit.
3.  **Zod Validation:** Validate all form inputs on both client and server.

---
*Template optimized for Semih Aydın's rapid development workflow.*
