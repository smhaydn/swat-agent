# Semih's Frontend Master Guide (React & Next.js)

> **Philosophy:** Modern, performant, and clean. No spaghetti code. 
> **Stack:** Next.js 15+, React 19, TypeScript, Shadcn/UI.

---

## 🏗️ 1. Modern Component Structure (The "Right Way")

**DO:**
*   Use **Server Components** by default. Only add `'use client'` when you need interactivity (onClick, useState).
*   Keep components small and focused (Single Responsibility).
*   Use **Composition Pattern** instead of passing 10 props.

**DON'T:**
*   ❌ Put complex logic inside `useEffect`. (Use Server Actions or React Query).
*   ❌ Prop drilling more than 2 levels. (Use Context or Zustand).
*   ❌ Use `any` type. (Define interfaces or types).

### ✅ Example: Server Action Form
```tsx
// actions.ts (Server Side)
'use server'
import { z } from 'zod'

const schema = z.object({ email: z.string().email() })

export async function subscribe(formData: FormData) {
  const parsed = schema.safeParse({ email: formData.get('email') })
  if (!parsed.success) return { error: 'Invalid email' }
  
  await db.subscribers.create({ email: parsed.data.email })
  return { success: true }
}

// SubscribeForm.tsx (Client Side)
'use client'
import { useFormState } from 'react-dom'
import { subscribe } from './actions'

export function SubscribeForm() {
  const [state, action] = useFormState(subscribe, null)
  
  return (
    <form action={action}>
      <input name="email" className="border p-2 rounded" />
      <button type="submit">Join</button>
      {state?.error && <p className="text-red-500">{state.error}</p>}
    </form>
  )
}
```

---

## ⚡ 2. Performance Optimization (Speed Matters)

*   **Images:** Always use `next/image` with `placeholder="blur"`.
*   **Fonts:** Use `next/font` (Google Fonts) to prevent layout shifts.
*   **Lazy Loading:** Use `dynamic(() => import(...))` for heavy components (charts, maps).
*   **Server Component Payload:** Don't pass huge JSON objects from Server to Client components. Pass only what's needed.

---

## 🎣 3. State Management (Zustand Rules)

Don't use Redux. Use **Zustand** for global state.

```ts
// store/use-cart.ts
import { create } from 'zustand'

type CartStore = {
  items: number
  addItem: () => void
}

export const useCart = create<CartStore>((set) => ({
  items: 0,
  addItem: () => set((state) => ({ items: state.items + 1 })),
}))
```

---

## 🎨 4. Styling (Tailwind + Shadcn)

*   **Utility First:** Use Tailwind classes directly.
*   **Conflict:** Use `cn()` helper (clsx + tailwind-merge) when merging classes.
*   **Variables:** Use CSS variables for theme colors (`bg-primary`, `text-muted-foreground`).

---
*Optimized for Semih Aydın's frontend workflow. 2026-02-13*
