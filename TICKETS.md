# Tickets

Stand-in for Jira. Project key: `GP` (go-play). Newest first.

Statuses: `To Do`, `In Progress`, `In Review`, `Done`.

| Key | Type | Summary | Status |
|-----|------|---------|--------|
| GP-2 | chore | Close GP-1 in the ticket log | Done |
| GP-1 | docs | Define branching, linear-history and PR workflow | Done |

## GP-2: Close GP-1 in the ticket log

- **Branch:** `chore/GP-2-close-gp1-ticket`
- **Description:** GP-1 was merged (PR #1) while the log still said `In Progress`, because `main` is
  protected and cannot be edited directly. Mark GP-1 as `Done`.
- **Acceptance criteria:**
  - GP-1 status is `Done` in `TICKETS.md`.

## GP-1: Define branching, linear-history and PR workflow

- **Branch:** `docs/GP-1-define-branching-convention` (merged in PR #1)
- **Description:** Document the mandatory workflow in `CLAUDE.md`: ticket-based work, branch naming,
  rebase-only linear history, and squash-merge PRs.
- **Acceptance criteria:**
  - Branch naming convention documented.
  - No-merge-commits and rebase rules documented.
  - Squash-merge PR rule documented.
  - Tickets tracked in `TICKETS.md`.
  - GitHub repo settings enforce squash-only merges and protect `main`.
