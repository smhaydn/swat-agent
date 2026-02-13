# 🎨 Semih's AI Art Master (ComfyUI)

> **Mission:** Transform words into pixel-perfect AI art using ComfyUI.
> **Tools:** ComfyUI API, Custom Nodes, Python, PyTorch.

---

## 🏗️ 1. ComfyUI Architecture (The Brain)

ComfyUI is not just a UI; it's a **Node-Based Graph Execution Engine**.

**Core Concept:**
*   **Workflow:** Instead of clicking buttons, we build a `.json` graph.
*   **Nodes:** Functions (Load Image, KSampler, Save Image).
*   **Links:** Data flow (LATENT -> VAE DECODE -> IMAGE).

---

## 🧩 2. Essential Custom Nodes (Semih's Toolkit)

Don't use vanilla nodes for everything. Use these power tools:

| Node Checkpoint | Purpose | Why? |
| :--- | :--- | :--- |
| **ComfyUI-Manager** | Dependency Manager | Auto-install missing nodes. |
| **ControlNet** | Structure Guide | Use Canny/Depth to keep shapes. |
| **IPAdapter** | Style Transfer | Copy face/style from reference image. |
| **Reactor** | Face Swap | Perfect for consistent characters. |
| **Ultimate SD Upscale** | High-Res Fix | 4x detail without hallucinations. |

---

## 🐍 3. API Integration (Python Control)

To automate ComfyUI, use the WebSocket API.

```python
# workflow_runner.py
import websocket
import json
import urllib.request
import uuid

server_address = "127.0.0.1:8188"
client_id = str(uuid.uuid4())

def queue_prompt(prompt_workflow):
    p = {"prompt": prompt_workflow, "client_id": client_id}
    data = json.dumps(p).encode('utf-8')
    req = urllib.request.Request(f"http://{server_address}/prompt", data=data)
    return json.loads(urllib.request.urlopen(req).read())

# Load your workflow.json and run it!
```

---

## ⚡ 4. Optimization Tips

*   **VRAM Management:** Use `--lowvram` flag only if <8GB GPU.
*   **Batch Size:** Increase batch size for faster generation (if VRAM allows).
*   **Preview:** Disable preview during batch processing to save resources.

---
*Added to S.W.A.T. Arsenal. 2026-02-13*
