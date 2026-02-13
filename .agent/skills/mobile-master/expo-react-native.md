# Semih's Mobile Master Guide (React Native / Expo)

> **Philosophy:** One codebase, two platforms (iOS + Android).
> **Stack:** Expo Router, NativeWind (Tailwind), React Native Reanimated.

---

## 📱 1. Setup (The Expo Way)

Forget manual Xcode/Android Studio builds. Use **Expo Prebuild**.

```bash
npx create-expo-app@latest my-app --template default
```

**Key Libraries:**
*   **Navigation:** `expo-router` (File-based routing like Next.js).
*   **Styling:** `nativewind` (Tailwind for Mobile).
*   **Icons:** `@expo/vector-icons`.

---

## ⚡ 2. Performance (60 FPS Rule)

Mobile apps must feel native.

*   **Animations:** Use `react-native-reanimated`. NEVER use `Animated` from React Native core for heavy stuff.
*   **Lists:** Always use `FlashList` (Shopify), not `FlatList`. It's 5x faster.
*   **Images:** Use `expo-image` with caching enabled.

---

## 🎨 3. Native Features (The "App" Feel)

*   **Haptics:** `expo-haptics` for vibration on button press.
*   **Gestures:** `react-native-gesture-handler` for swipe-to-delete.
*   **Safe Area:** Always wrap screens in `<SafeAreaView>`.

---

## 🚀 4. Deployment (EAS Build)

Don't buy a Max just for iOS builds. Use **Expo Application Services (EAS)**.

```bash
eas build --platform ios --profile production
eas build --platform android --profile production
```

This generates `.ipa` and `.apk` files in the cloud.

---
*Optimized for Semih Aydın's Mobile Workflow. 2026-02-13*
