# Project Type Detection

> Analyze user requests to determine project type and template.

## Keyword Matrix

| Keywords | Project Type | Template |
|----------|--------------|----------|
| dashboard, panel, management, app, fullstack | Web App (Full-Stack) | nextjs-fullstack |
| saas, subscription, stripe, startup | SaaS Product | nextjs-saas |
| landing, portfolio, static, marketing | Static Site | nextjs-static |
| python, fastapi, data, ml | Python API | python-fastapi |
| mobile, android, ios, app | Mobile App | react-native-app |
| monorepo, workspace, turbo | Monorepo | monorepo-turborepo |

## Detection Process

```
1. Tokenize user request
2. Extract keywords
3. Determine project type
4. Detect missing information → forward to conversation-manager
5. Suggest tech stack
```
