# Tickets

Stand-in for Jira. Project key: `GP` (go-play). Newest first.

Statuses: `To Do`, `In Progress`, `In Review`, `Done`.

| Key | Type | Summary | Status |
|-----|------|---------|--------|
| GP-4 | docs | Design and specify Axioma Account and Auth service (spec-driven) | In Progress |
| GP-3 | docs | Draft Axioma Account Service foundations and open questions | Done |
| GP-2 | chore | Close GP-1 in the ticket log | Done |
| GP-1 | docs | Define branching, linear-history and PR workflow | Done |

## GP-4: Design and specify Axioma Account and Auth service

- **Branch:** `docs/GP-4-account-auth-design`
- **Tier:** spec-driven (GitHub Spec Kit)
- **Description:** Resolve the open questions in `docs/domain/axioma-account-service.md`, then
  specify and plan the Account Service (accounts, tenants, invitations) together with the Auth
  Service (users, memberships, tokens, roles) as one Go codebase with a logical separation.
  Design and spec only: **implementation is split into follow-up tickets** (GP-5 onward), created
  from the Spec Kit task list so each slice is one branch and one PR.
- **Scope change:** originally `feat` and included implementation. Narrowed to `docs` to keep the PR
  reviewable (one ticket = one branch = one PR).
- **Acceptance criteria:**
  - All open questions in the domain doc are resolved or explicitly deferred.
  - Spec Kit installed, and its branch naming and `specs/` layout reconciled with `CLAUDE.md`.
  - Spec and plan written for the Account and Auth services.
  - Implementation tickets created in `TICKETS.md`.
- **Progress:** Q1 to Q9 and Q16 resolved. Remaining: Q10 to Q15 (lifecycle, Mexico-specific,
  technical), then Spec Kit.

## GP-3: Draft Axioma Account Service foundations and open questions

- **Branch:** `docs/GP-3-axioma-account-foundations`
- **Description:** Capture the core concepts (Customer, Subscription, AxiomaAccount, Tenant, User,
  SuperUser), a draft relationship model, and the open questions for the next ticket. No design
  decisions yet.
- **Acceptance criteria:**
  - Concepts and a draft relationship model documented in `docs/domain/axioma-account-service.md`.
  - Open questions listed and grouped.
  - Follow-up ticket GP-4 created.

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
