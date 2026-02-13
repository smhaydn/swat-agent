---
name: app-builder
description: Main application building orchestrator. Creates full-stack applications from natural language requests. Determines project type, selects tech stack, coordinates agents.
allowed-tools: Read, Write, Edit, Glob, Grep, Bash, Agent
---

# App Builder - Application Building Orchestrator

> Analyzes user's requests, determines tech stack, plans structure, and coordinates agents.

## 🎯 Selective Reading Rule

**Read ONLY files relevant to the request!** Check the content map, find what you need.

| File | Description | When to Read |
|------|-------------|--------------|
| `project-detection.md` | Keyword matrix, project type detection | Starting new project |
| `tech-stack.md` | 2026 default stack, alternatives | Choosing technologies |
| `agent-coordination.md` | Agent pipeline, execution order | Coordinating multi-agent work |
| `scaffolding.md` | Directory structure, core files | Creating project structure |
| `feature-building.md` | Feature analysis, error handling | Adding features to existing project |
| `templates/SKILL.md` | **Project templates** | Scaffolding new project |

---

## 📦 Templates (Semih's Core Stack)

Quick-start scaffolding for new projects. **Only the best tools are kept.**

| Template | Tech Stack | When to Use |
|----------|------------|-------------|
| **[nextjs-semih-stack](templates/nextjs-semih-stack/TEMPLATE.md)** | **Next.js + Supabase + Shadcn** | **Recommended (Semih's Stack)** |
| [nextjs-fullstack](templates/nextjs-fullstack/TEMPLATE.md) | Next.js + Prisma + Tailwind | Default Choice (Web App) |
| [nextjs-saas](templates/nextjs-saas/TEMPLATE.md) | Next.js + Stripe + Auth | SaaS Product |
| [nextjs-static](templates/nextjs-static/TEMPLATE.md) | Next.js + Framer Motion | Landing Page |
| [python-fastapi](templates/python-fastapi/TEMPLATE.md) | FastAPI + Pydantic | Python API / Data Science |
| [react-native-app](templates/react-native-app/TEMPLATE.md) | Expo + Zustand | Mobile App |
| [monorepo-turborepo](templates/monorepo-turborepo/TEMPLATE.md) | Turborepo + pnpm | Advanced Multi-package Project |

---

## 🔗 Related Agents

| Agent | Role |
|-------|------|
| `project-planner` | Task breakdown, dependency graph |
| `frontend-specialist` | UI components, pages |
| `backend-specialist` | API, business logic |
| `database-architect` | Schema, migrations |
| `devops-engineer` | Deployment, preview |

---

## Usage Example

```
User: "Make an Instagram clone with photo sharing and likes"

App Builder Process:
1. Project type: Social Media App
2. Tech stack: Next.js + Prisma + Cloudinary + Clerk
3. Create plan:
   ├─ Database schema (users, posts, likes, follows)
   ├─ API routes (12 endpoints)
   ├─ Pages (feed, profile, upload)
   └─ Components (PostCard, Feed, LikeButton)
4. Coordinate agents
5. Report progress
6. Start preview
```
