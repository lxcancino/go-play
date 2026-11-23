# go-play

A Go monorepo for learning and practicing Go through realistic, industry-style web APIs.

Each project is a small, self-contained demo (different web frameworks, auth patterns,
persistence, testing, etc.) that tackles challenges commonly found in real-world backends.

> Status: skeleton only. No projects yet. The demo theme and first project are still to be defined.

## Goals

- Practice idiomatic Go with realistic scenarios, starting from very simple endpoints.
- Compare web frameworks (Fiber first, possibly Echo and Gin later).
- Cover common industry concerns: persistence (PostgreSQL), authentication and authorization,
  validation, error handling, configuration, logging, testing, and observability.

## Repository layout

```
go-play/
├── go.work          # Go workspace listing every module (local development)
├── Taskfile.yml     # Repo-wide commands (see below)
├── CLAUDE.md        # Guidance for Claude Code
├── README.md
└── <project>/       # One directory per demo project, each with its own go.mod
    ├── go.mod
    ├── cmd/<app>/   # Entry points
    └── internal/    # Private application code
```

Each project is its own Go module so projects can use different frameworks and
dependencies without affecting each other. `go.work` ties them together locally.

## Prerequisites

- [Go](https://go.dev/dl/) 1.27+
- [Task](https://taskfile.dev/installation/) (`brew install go-task`)
- [Docker](https://docs.docker.com/get-docker/) (for PostgreSQL, once projects need it)

## Common commands

```sh
task          # list available tasks
task fmt      # format all modules
task vet      # go vet on all modules
task test     # run tests on all modules
task tidy     # go mod tidy on all modules
```

## Adding a project

```sh
mkdir my-project && cd my-project
go mod init github.com/<user>/go-play/my-project
cd .. && go work use ./my-project
```

## Projects

_None yet._
