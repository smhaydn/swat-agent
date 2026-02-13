# Semih's Desktop Wizard Guide (Electron / Tauri)

> **Philosophy:** Web technologies, desktop power.
> **Tools:** Electron Forge (Standard), Tauri (Lightweight).

---

## 🏗️ 1. Modern Desktop Setup (Electron Forge)

Start with the best tooling.

```bash
npm init electron-app@latest my-app -- --template=typescript
```

**Auto-Update:** Use `electron-updater` with GitHub Releases. It's free and works.

---

## 🔒 2. Security (Don't Get Hacked)

Electron is powerful but dangerous.

*   **Context Isolation:** ALWAYS `contextIsolation: true`.
*   **Node Integration:** NEVER `nodeIntegration: true` in Renderer process.
*   **CSP:** Set strict Content Security Policy.

---

## 🔌 3. Native Integration (The Magic)

*   **System Tray:** App stays open in background.
*   **Global Shortcuts:** Register hotkeys (`Ctrl+Shift+X`).
*   **File System:** Use `IPC` (Inter-Process Communication) to read/write files safely.

```ts
// main.ts (Node.js Process)
ipcMain.handle('read-file', async (event, path) => {
  return fs.readFileSync(path, 'utf-8')
})

// renderer.ts (React Component)
const content = await window.electronAPI.readFile('/path/to/file')
```

---

## 📦 4. Building .exe / .dmg

Use **Electron Forge** makers.

```json
"makers": [
  {
    "name": "@electron-forge/maker-squirrel",
    "config": {
      "name": "my_app"
    }
  }
]
```
 Run `npm run make` to get your installers.

---
*Optimized for Semih Aydın's Desktop Workflow. 2026-02-13*
