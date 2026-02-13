# SWAT-Agent Output Contract

**Version:** 1.0.0
**Enforcement:** MANDATORY for all agents (Specialists & Meta-Agents).

## 1. Core Philosophy
Every agent output must be structured, deterministic, and parseable. We do not "chat"; we "execute" and "report".
This contract ensures that the Chief Strategist can seamlessly merge outputs from multiple agents.

## 2. JSON Structure
All agents MUST wrap their final response in a JSON block (or equivalent structured markdown section if pure JSON is too rigid for the LLM, but JSON is preferred).

```json
{
  "intent": "Brief summary of what this response addresses",
  "context_summary": "1-2 sentences on current state/context",
  "plan": [
    "Step 1: description",
    "Step 2: description"
  ],
  "execution": {
    "actions_taken": [
      "Created file X",
      "Modified function Y"
    ],
    "tools_used": ["write_to_file", "run_command"]
  },
  "risks_and_failure_modes": [
    "Risk 1: API rate limit",
    "Risk 2: User input validation missing"
  ],
  "validation_checks": [
    "Check 1: File exists",
    "Check 2: Linter passes"
  ],
  "confidence_score": 0.95,
  "assumptions": [
    "User has Node.js installed",
    "DB is running on localhost:5432"
  ],
  "unknowns": [
    "Exact version of dependency Z"
  ],
  "next_actions": [
    "User must run 'npm install'",
    "Review file X"
  ],
  "artifacts_written": [
    "/absolute/path/to/file1.ts",
    "/absolute/path/to/file2.md"
  ]
}
```

## 3. Field Definitions

| Field | Type | Description |
| :--- | :--- | :--- |
| `intent` | string | The user's goal or sub-goal this output satisfies. |
| `context_summary` | string | Brief recap of the situation. |
| `plan` | array | The theoretical steps planned. |
| `execution` | object | Actual work done. |
| `risks_and_failure_modes` | array | **CRITICAL**: What could go wrong? (Input for Failure Engineer) |
| `validation_checks` | array | How we know it works. |
| `confidence_score` | number | 0.00 to 1.00. < 0.8 trigger manual review. |
| `assumptions` | array | Implicit factors relied upon. |
| `unknowns` | array | Information missing or guessed. |
| `next_actions` | array | Handover to user or next agent. |
| `artifacts_written` | array | List of ALL files created or modified. |

## 4. Examples

### Example: Frontend Task
```json
{
  "intent": "Create a responsive login component",
  "context_summary": "User requested a login form with email/password validation.",
  "plan": [
    "Design UI structure",
    "Implement Zod validation",
    "Connect to auth hook"
  ],
  "execution": {
    "actions_taken": ["Created components/LoginForm.tsx"],
    "tools_used": ["write_to_file"]
  },
  "risks_and_failure_modes": ["Mobile layout might overflow on small screens"],
  "validation_checks": ["Validated form submits only with valid email"],
  "confidence_score": 0.98,
  "assumptions": ["Tailwind CSS is installed"],
  "unknowns": [],
  "next_actions": ["Import LoginForm in page.tsx"],
  "artifacts_written": ["/src/components/LoginForm.tsx"]
}
```

### Example: Security Review
```json
{
  "intent": "Audit API for IDOR",
  "context_summary": "Checking user profile endpoint for unauthorized access.",
  "execution": {
    "actions_taken": ["Analyzed route handler", "Simulated unauthorized request"],
    "tools_used": ["read_file", "code_analysis"]
  },
  "risks_and_failure_modes": ["RLS policy might be too permissive"],
  "confidence_score": 0.85,
  "artifacts_written": []
}
```
