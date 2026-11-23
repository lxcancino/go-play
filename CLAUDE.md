# go-play

Go monorepo for learning Go by building realistic web APIs. The goal is practice and
understanding, not shipping a product. Prefer clear, idiomatic code and explain the "why"
behind Go techniques when introducing them.

## Status

Skeleton only. The demo theme/domain and the first project are not defined yet. Do not invent
projects or domain details; ask first.

## Structure

- One directory per project at the repo root, each its own Go module (own `go.mod`).
- `go.work` at the root lists all modules for local development. Run `go work use ./<project>`
  when adding one.
- Shared code, if ever needed, goes in its own module (e.g. `shared/`), not copied between projects.
- Inside a project: `cmd/<app>/main.go` for entry points, `internal/` for private code.

## Commands

Task is the task runner (`Taskfile.yml`): `task fmt`, `task vet`, `task test`, `task tidy`.
These loop over every module because Go has no built-in "all workspace modules" command.
Inside a project, plain `go test ./...` and `go run ./cmd/<app>` work as usual.

## Go conventions

- Idiomatic Go: small interfaces defined where they are used, accept interfaces and return structs,
  wrap errors with `%w`, pass `context.Context` as the first parameter.
- Keep `main` thin: wire configuration, dependencies and the server, nothing more.
- Table-driven tests; run `go vet` and `gofmt` before considering work done.
- Configuration via environment variables; never commit secrets (`.env` is gitignored,
  provide `.env.example`).
- PostgreSQL runs in Docker for local development.
- Start simple. Add layers (services, repositories, etc.) only when a project needs them, and
  say why.

## Working style

- Go step by step; confirm design decisions with the user before building.
- Pin dependency versions through `go.mod`; avoid adding libraries without explaining the choice.

## Git

Always use the Conventional Commits pattern for commit messages:

- Format: `<type>: <short description>`, with an optional bullet-list body.
- Types: `feat`, `fix`, `docs`, `refactor`, `test`, `chore`, `build`, `ci`.
- Imperative, lowercase description, no trailing period.
- No ticket numbers.
- End every commit message with the `Co-Authored-By` trailer for Claude.
- Never commit without showing the changes and the proposed message first, and asking.

These mirror the global rules in `~/.claude-personal/CLAUDE.md`.

## Workflow (mandatory)

We work as in a Jira-driven team. Every change starts from a ticket. These rules are mandatory;
if a request conflicts with them, say so and ask before proceeding.

### Tickets

- Tickets use the key `GP-<n>` (sequential) and are logged in `TICKETS.md` (a stand-in for Jira).
- Create or update the ticket in `TICKETS.md` before starting work. Never work without a ticket.
- Ticket numbers go in branch names, PR titles and `TICKETS.md`, never in commit messages.

### Branches

- Never commit directly to `main`. Branch from an up-to-date `main`; one ticket = one branch = one PR.
- Naming: `<type>/GP-<n>-<short-kebab-description>`, e.g. `feat/GP-12-customer-crud-endpoints`.
- `<type>` uses the same list as Conventional Commits. Description is lowercase kebab-case, ~5 words max.
- Only one slash in the name.

### Linear history (no merge commits, ever)

- Keep branches current by rebasing onto `main` (`git fetch && git rebase origin/main`), never by
  merging `main` into the branch. `git pull` is configured to rebase.
- Never create merge commits. Do not use `git merge` (except fast-forward) or the "Create a merge commit"
  button.
- After a rebase, push with `git push --force-with-lease` (never plain `--force`), and only on your own
  ticket branch, never on `main`.

### Pull requests

- Every branch is merged through a PR into `main`, and only by squash merge
  (`gh pr merge --squash --delete-branch`).
- PR title is a Conventional Commit (`<type>: <short description>`) because it becomes the squashed
  commit on `main`. Put the ticket key (`GP-<n>`) in the PR body.
- The PR body becomes the squashed commit body, so end it with the `Co-Authored-By` trailer for Claude.
- Delete the branch after merging.
- Commits still require the user's approval (see Git above). Once committed, ticket branches may be
  pushed and PRs opened without asking.
- Always ask the user before merging a PR into `main`.

### GitHub enforcement

The repo settings back these rules up: squash merge only, branches deleted on merge, and `main` is
protected (PR required, linear history, no force pushes or deletions, enforced for admins).
If a push or merge is rejected by these rules, do not work around them; fix the workflow.
