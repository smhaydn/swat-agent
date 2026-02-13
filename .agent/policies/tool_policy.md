# SWAT-Agent Tool Policy

**Enforcement:** MANDATORY for all agents.

## 1. Global Safety Rules (The clean hands doctrine)

1.  **NEVER Output Secrets:** API keys, passwords, and private tokens must NEVER be printed in cleartext in logs, thoughts, or final outputs. Mask them: `sk-****`.
2.  **No Destructive Deletes:** Do not use `rm -rf` or equivalent on user directories without explicit confirmation or backup.
3.  **Sandboxed Execution:** Prefer running commands in the project root. Do not navigate to system directories (`/etc`, `C:\Windows`).
4.  **Escalation Protocol:** If a tool fails or is missing (e.g., `npm` not found), do NOT fake it. Report it in `risks_and_failure_modes` and lower `confidence_score`.

## 2. Role-Based Tool Access

| Agent Role | Allowed Tools (Conceptual) | Forbidden Tools |
| :--- | :--- | :--- |
| **Chief Strategist** | `read_file`, `list_dir`, `task_delegation`, `memory_read` | `write_to_file` (code), `run_command` (builds) |
| **Internal Auditor** | `read_file`, `grep_search`, `lint_check` | `write_to_file` (except audit reports), `run_command` (destructive) |
| **Failure Engineer** | `read_file`, `simulation_run` | `deploy_production` |
| **App Builder** | ALL Development Tools | None |
| **Frontend Master** | `write_to_file` (tsx/css), `npm run dev` | Backend DB migrations |
| **Backend Ninja** | `write_to_file` (py/sql), `migration_tool` | UI Styling tools |
| **Security Guard** | `code_scan`, `dependency_check` | `write_to_file` (feature code) |

## 3. Tool Usage Best Practices

- **Atomic Writes:** When writing code, write the complete valid file or a unified diff. Do not leave files in a broken state.
- **Verification:** After running a command (e.g., `npm install`), ALWAYS check the exit code/result.
- **Idempotency:** Tool calls should be safe to retry if possible.

## 4. Output Integration

All tool usage must be logged in the `execution.tools_used` field of the Output Contract.
