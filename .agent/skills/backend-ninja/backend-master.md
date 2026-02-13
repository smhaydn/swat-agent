# Semih's Performance Engine (Next.js & Supabase)

> **Philosophy:** Blazing fast. Secure by default. Scale to millions.
> **Tools:** Supabase (Postgres), Prisma, Edge Functions, Redis (Upstash).

---

## ⚡ 1. Database Architecture (Supabase Only)

**DO:**
*   **RLS (Row Level Security):** This is NOT optional. Every table must have policies.
    ```sql
    create policy "Users can see own data" on my_table 
    for select using (auth.uid() = user_id);
    ```
*   **Indexing:** Add index to columns used in `WHERE`, `ORDER BY`, or `JOIN`.
*   **Edge Functions:** Use Deno functions for heavy lifting (Image processing, complex calculations).

**DON'T:**
*   ❌ Use stored procedures unless critical. Keep logic in App code or Edge functions.
*   ❌ `select * from users`. Select only fields you need.

---

## 🌐 2. API Strategy (Next.js App Router)

### A. Server Actions (Mutation)
For creates/updates, use Server Actions directly. No need for `/api/create-user` endpoint. It's faster and type-safe.

```ts
// actions.ts
'use server'
export async function updateUser(id: string, data: UserUpdate) {
  // Validate -> Auth Check -> DB Update -> Revalidate Path
}
```

### B. Route Handlers (Public API / Webhooks)
Use `/app/api/...` **ONLY** for:
1.  **Webhooks** (Stripe, LemonSqueezy)
2.  **Public API** (Mobile App, External Partners)
3.  **Cron Jobs** (Vercel Cron)

---

## 🚀 3. Caching Strategy (The Speed Secret)

*   **Static (Default):** `fetch('...', { cache: 'force-cache' })`. Use for blogs, pricing pages.
*   **Revalidate:** `fetch('...', { next: { revalidate: 3600 } })`. Good for dashboards (1 hour cache).
*   **Dynamic:** `export const dynamic = 'force-dynamic'`. Use for Auth-protected user data.

---

## 🐍 4. Python Integration (AI & Data)

When Python is needed (FastAPI):
*   Keep it separate (Microservice).
*   Protect endpoints with `API_SECRET_KEY`.
*   Use `Pydantic` for strict data validation.

---
*Optimized for Semih Aydın's high-performance backend needs. 2026-02-13*
