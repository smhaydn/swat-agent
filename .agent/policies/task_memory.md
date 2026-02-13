# SWAT-Agent Task Memory System

**Purpose:** To create a persistent, debuggable, and auditable history of every "mission" the agents undertake.

## 1. Directory Structure

All task artifacts are stored in `.task_runs/`. This folder should be `.gitignore`'d if it gets too large, but currently, we keep it for value alignment and debugging.

**Pattern:**
`.task_runs/<YYYY-MM-DD>/<task_slug>/`

- `<YYYY-MM-DD>`: Date of execution.
- `<task_slug>`: A kebab-case summary of the task (e.g., `fix-login-modal`, `audit-payments-api`).

## 2. Required Artifacts

Inside the task folder, the system must generate:

1.  **`intent.md`**
    - The raw user prompt and the "Chief Strategist" interpretation of it.

2.  **`decisions.md`**
    - Key architectural choices made (e.g., "Chose React Query over SWR because...").

3.  **`plan.md`**
    - The initial plan and any mid-flight course corrections.

4.  **`final_output.md`**
    - A human-readable summary of what was delivered.

5.  **`audit.md`** (Optional but recommended)
    - The Internal Auditor's report.

6.  **`failure_premortem.md`** (Optional but recommended)
    - The Failure Engineer's analysis of what *could* go wrong.

## 3. Writer Implementation (Lightweight)

Agents do not need a complex database. They simply write specific markdown files to this path.

**Example `intent.md`:**
```markdown
# Task: Fix Login Modal
**User Request:** "The login modal doesn't close when I click outside."
**Interpretation:** Frontend bug. Event listener missing or z-index issue.
**Assigned To:** Frontend Master
```

## 4. Lifecycle

1.  **Start:** Chief Strategist creates the folder and `intent.md`.
2.  **Execution:** Specialist agents append to `decisions.md` and `plan.md`.
3.  **Review:** Internal Auditor writes `audit.md`.
4.  **Completion:** System writes `final_output.md`.
