# Semih's Security Protocol (Defense Matrix)

> **Philosophy:** Trust no one. Validate everything. Secure by default.
> **Tools:** Zod, Supabase RLS, Content Security Policy (CSP).

---

## 🛡️ 1. Input Validation (Zod Everywhere)

**NEVER** trust user input. Validate `req.body`, `params`, and `searchParams`.

```ts
// schema.ts
import { z } from 'zod';

export const UserSchema = z.object({
  email: z.string().email().min(5),
  password: z.string().min(12, "Password must be strong!"),
  role: z.enum(['user', 'admin']).default('user'),
});

// usage
const result = UserSchema.safeParse(req.body);
if (!result.success) throw new Error("Hack attempt blocked!");
```

---

## 🔒 2. Database Protection (Supabase RLS)

**Rule:** Every table MUST have RLS enabled. No exceptions.

*   ✅ **Policy:** Only user can edit their own profile.
    ```sql
    create policy "Update Own Profile" on profiles
    for update using (auth.uid() = id);
    ```
*   ✅ **Service Role:** Use `supabaseAdmin` client strictly for backend tasks (cron jobs), never in client.

---

## 🔑 3. Secrets Management

*   **Rule:** `.env` files are ignored in git.
*   **Rule:** API Keys (Stripe Secret, Supabase Service Role) stay on server. Next.js creates a boundary automatically if variable doesn't start with `NEXT_PUBLIC_`.
*   **Audit:** Run `git grep "sk_test_"` periodically to find leaked keys.

---

## 🚫 4. Attack Prevention

*   **XSS (Cross Site Scripting):** React escapes HTML by default. Be careful with `dangerouslySetInnerHTML`.
*   **CSRF:** Next.js Server Actions handle CSRF automatically.
*   **Rate Limiting:** Protect login routes (Limit: 5 tries/min).

---
*Optimized for Semih Aydın's secure application standards. 2026-02-13*
