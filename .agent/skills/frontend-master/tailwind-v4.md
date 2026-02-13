# Semih's Tailwind CSS v4 Master Guide

> **Philosophy:** Write styles as variables. Use container queries. No random values.

---

## 🌪️ 1. Tailwind v4 New Features (Learn This)

### A. Container Queries (`@container`)
*   **Why:** Instead of sizing based on screen (`md:`), size based on parent (`@lg:`).
*   **Usage:**
    ```html
    <div className="@container">
      <div className="@lg:flex-row flex-col flex">...</div>
    </div>
    ```

### B. Logical Properties
*   **Why:** Better for multi-language support (RTL).
*   **Usage:**
    *   `ml-4` (Left) → `ms-4` (Start)
    *   `mr-4` (Right) → `me-4` (End)

---

## 📐 2. Layout Patterns (Grid > Flex)

**Grid is King for structured layouts.**

*   **Responsive Grid:** `grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6`
*   **Auto-Fit:** `grid grid-cols-[repeat(auto-fit,minmax(250px,1fr))]` (Responsive cards without media queries).

---

## 🎨 3. Color Palette (Use Variables)

Don't hardcode hex codes. Use CSS variables defined in `globals.css`.

*   ✅ `bg-background text-foreground`
*   ✅ `border-border`
*   ❌ `bg-[#fff] text-[#000]`

---

## 🎭 4. Animation & Interaction

*   **Group Hover:** `group` parent + `group-hover:opacity-100` child.
*   **Peer Focus:** Input `peer` + Label `peer-focus:-translate-y-4` (Floating label).
*   **Duration:** Use `duration-300 ease-in-out` for smooth transitions.

---
*Optimized for Semih Aydın's modern CSS workflow. 2026-02-13*
