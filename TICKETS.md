# Tickets

Stand-in for Jira. Project key: `GP` (go-play). Newest first.

Statuses: `To Do`, `In Progress`, `In Review`, `Done`.

| Key | Type | Summary | Status |
|-----|------|---------|--------|
| GP-1 | docs | Define branching, linear-history and PR workflow | In Progress |

## GP-1: Define branching, linear-history and PR workflow

- **Branch:** `docs/GP-1-define-branching-convention`
- **Description:** Document the mandatory workflow in `CLAUDE.md`: ticket-based work, branch naming,
  rebase-only linear history, and squash-merge PRs.
- **Acceptance criteria:**
  - Branch naming convention documented.
  - No-merge-commits and rebase rules documented.
  - Squash-merge PR rule documented.
  - Tickets tracked in `TICKETS.md`.
  - GitHub repo settings enforce squash-only merges and protect `main`.
