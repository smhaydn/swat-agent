# Ultra Realism & AI Influencer Master Guide (Flux.1 / SDXL)

> **Mission:** 100% Photorealism. Indistinguishable from reality.
> **Key Tech:** Flux.1 Dev, LoRA Training (Kohya_ss), IDM-VTON, Reactor.

---

## 📸 1. The "Real Human" Recipe (Flux.1 Dev)

Forget SD 1.5. For 100% realism, use **Flux.1 Dev** or fine-tuned SDXL (Juggernaut XL).

**Prompt Secrets for Skin Texture:**
*   **Positive:** `raw photo, 8k uhd, dslr, soft lighting, high quality, film grain, Fujifilm XT3`
*   **Negative:** `3d render, plastic skin, smooth skin, cartoon, anime`

**The "Noise Injection" Trick:**
Add a `Ksampler` with `denoise: 0.3` after the first pass to add natural imperfections (pores, fuzz). Perfect skin looks fake.

---

## 👗 2. Virtual Try-On (VTON) & Fashion

To dress your AI Influencer in real products:

1.  **IDM-VTON Node:** The current SOTA for virtual try-on.
2.  **Workflow:**
    *   Input 1: Model Image (Your Influencer).
    *   Input 2: Garment Image (The Product).
    *   Mask: Use `SegmentAnything (SAM)` to auto-mask the body part.
3.  **Detail Fix:** If the logo is blurry, use `Inpaint` with `ControlNet (Tile)` on the logo area only.

---

## 👤 3. AI Influencer Consistency (Same Face Every Time)

How to keep the character identical across 100 photos:

1.  **Train a LoRA:**
    *   Take 15-20 varied photos of the face.
    *   Train using **Kohya_ss**.
    *   Trigger word: `ohwx woman`.
2.  **Reactor / IPAdapter FaceID:**
    *   Even with LoRA, faces drift.
    *   Use **Reactor Node** as the final step to swap the *original* face back onto the generation. This guarantees 100% identity match.

---

## 🎥 4. Video Generation (Sora / Kling Level)

*   **Image-to-Video:** Use `SVD (Stable Video Diffusion)` XT 1.1.
*   **Motion Bucket ID:** Keep it `127` for natural movement. Higher = shaky camera.

---
*Optimized for Semih Aydın's Ultra-Realistic AI Workflow. 2026-02-13*
