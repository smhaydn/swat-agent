# Semih's GSAP Animation Master Guide

> **Philosophy:** Use GSAP for complex, scroll-driven, cinematic animations.
> **Tool:** `@gsap/react`, `gsap`, `ScrollTrigger`.

---

## 🏎️ 1. Modern Setup (useGSAP Hook)

Don't use `useEffect`. Use the official `useGSAP` hook for React clean-up automatically.

```tsx
'use client'
import { useRef } from 'react'
import gsap from 'gsap'
import { useGSAP } from '@gsap/react'

export default function Hero() {
  const container = useRef(null)

  useGSAP(() => {
    // Write your vanilla GSAP code here
    gsap.to('.box', { x: 300, rotation: 360, duration: 2 })
  }, { scope: container }) // Auto-cleanup and scope selection

  return (
    <div ref={container} className="h-screen bg-black text-white">
      <div className="box w-20 h-20 bg-blue-500 rounded-xl" />
    </div>
  )
}
```

---

## 🎬 2. Cinematic Text Reveal (Stagger)

Make text arrive letter by letter or word by word.

```tsx
// Using SplitType + GSAP
useGSAP(() => {
  const chars = new SplitType('.title', { types: 'chars' }).chars
  
  gsap.from(chars, {
    y: 100,
    opacity: 0,
    stagger: 0.05,
    duration: 1,
    ease: 'power4.out',
    scrollTrigger: {
      trigger: '.hero-section',
      start: 'top center',
    }
  })
})
```

---

## 📜 3. ScrollTrigger (The Magic)

Trigger animations as you scroll down.

*   **Scrub:** Tie animation to scroll position (like a video player).
*   **Pin:** Lock an element while scrolling past (Apple-style product page).

```tsx
useGSAP(() => {
  gsap.to('.video', {
    scale: 1,
    borderRadius: '0%',
    scrollTrigger: {
      trigger: '.container',
      start: 'top boottom', // when top of element hits bottom of viewport
      end: 'top top',       // when top of element hits top of viewport
      scrub: true,          // smooth scrubbing
    }
  })
})
```

---

## ⚡ 4. Best Practices

*   **Don't Overdo It:** Animations should serve the content, not distract.
*   **Performance:** Animate `transform` (x, y, scale, rotation) and `opacity`. Avoid animating `width`, `height`, `top`, `left` (Layout Thrashing).
*   **Mobile:** Disable heavy scroll animations on mobile if performance drops.

---
*Added to Semih Aydın's frontend arsenal. 2026-02-13*
