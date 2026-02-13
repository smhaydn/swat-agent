# Semih's Web Vitals Master Guide

> **Goal:** Green scores on PageSpeed Insights (Lighthouse 100).
> **Focus:** LCP (Loading), FID (Interactivity), CLS (Stability).

---

## ⚡ 1. Critical Performance Audits

1.  **LCP (Largest Contentful Paint):** Check hero image.
    *   ✅ Use `<Image priority>` from `next/image`.
    *   ✅ Use WebP/AVIF formats.
    *   ❌ Don't lazy load the LCP element.
2.  **CLS (Cumulative Layout Shift):** Prevent elements from jumping.
    *   ✅ Reserve space for images/ads (`width` & `height` props).
    *   ✅ Use `min-height` for dynamic content.
3.  **Bundle Size:** Keep JS minimal.
    *   ✅ Use `@next/bundle-analyzer` to find heavy packages.
    *   ✅ Replace `moment.js` with `date-fns`.
    *   ✅ Import icons individually (`lucide-react/dist/esm/icons/home`).

---

## 🔍 2. Modern SEO (2026 Strategy)

*   **Metadata:** Use `generateMetadata()` in `layout.tsx` for dynamic Open Graph tags.
*   **Sitemap:** Generate `sitemap.ts` automatically.
*   **Semantic HTML:** exclusively use `<header>`, `<main>`, `<footer>`, `<article>`. Not just `<div>`.
*   **Accessibility (A11Y):** Every `img` needs `alt`. Colors need contrast.

---

## 🚦 3. Edge Optimization (Supabase + Vercel)

*   **Middleware:** Process auth checks at the Edge (closer to user).
*   **ISR (Incremental Static Regeneration):** Cache pages but update them periodically (`revalidate: 60`).
*   **Fonts:** `next/font` automatically optimizes Google Fonts (Self-hosted, zero layout shift).

---
*Optimized for Semih Aydın's high-speed web apps. 2026-02-13*
