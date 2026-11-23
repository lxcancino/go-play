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
