# Semih's Modern UI/UX Master Guide

> **Philosophy:** Beautiful, accessible, and responsive. No ugly templates.
> **Tools:** Figma, Tailwind CSS, Lucide Icons.

---

## 🎨 1. Core Principles (The Vibe)

*   **Clean & Minimal:** Whitespace is your friend. Don't crowd the screen.
*   **Hierarchical:** Use font weight (Bold > Medium > Regular) and color (Black > Gray 500 > Gray 400) to guide the eye.
*   **Consistency:** Buttons on page A must look like buttons on page B. (Use Shadcn/UI for this).

---

## 📱 2. Mobile-First (Responsive Rules)

**ALWAYS** write styles for mobile first, then add breakpoints for larger screens.

❌ **Wrong:**
```html
<div class="w-1/2 md:w-full"> <!-- Desktop first thinking -->
```

✅ **Right:**
```html
<div class="w-full md:w-1/2 lg:w-1/3"> <!-- Mobile first thinking -->
```
*   **Touch Targets:** Buttons must be at least **44x44px** on mobile.
*   **Font Size:** Body text min 16px (prevent iOS zoom).

---

## 🌈 3. Color Theory (Semih's Palette)

Avoid default HTML colors. Use this system:

| Role | Tailwind Class | Usage |
| :--- | :--- | :--- |
| **Primary** | `bg-zinc-900 text-white` | Main CTA Buttons |
| **Secondary** | `bg-white border text-zinc-900` | Cancel / Outline Buttons |
| **Accent** | `bg-blue-600 text-white` | Highlights / Links |
| **Destructive** | `bg-red-500 text-white` | Delete / Warning |
| **Muted** | `text-zinc-500` | Subtitles / Hints |

*   **Dark Mode:** Use `dark:` classes everywhere. Test both themes.

---

## ✨ 4. Micro-Interactions (The Magic)

Don't make a static page. Make it feel alive.

*   **Hover:** `hover:brightness-95` on buttons.
*   **Active:** `active:scale-95` on click (tactile feel).
*   **Focus:** `focus-visible:ring-2` for accessibility.
*   **Transitions:** Add `transition-all duration-200` to interactive elements.

---

## 🖼️ 5. Typography

*   **Headings:** Establish clear hierarchy (H1 > H2 > H3).
*   **Line Height:** Use `leading-tight` for headings, `leading-relaxed` for paragraphs.
*   **Tracking:** Use `tracking-tight` (-0.02em) for modern, professional headings.

---
*Optimized for Semih Aydın's design standards. 2026-02-13*
