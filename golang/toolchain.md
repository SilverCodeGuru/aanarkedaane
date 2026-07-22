# Go toolchain cheat sheet

Quick reference for `GOTOOLCHAIN`, version switching, and local dev setup.
Official source: https://go.dev/doc/toolchain

---

## Mental model

```
PATH → bootstrap go (/usr/local/go/bin/go)
         ↓
      read go.mod / go.work in current directory
         ↓
      GOTOOLCHAIN decides: bootstrap only, or switch?
         ↓
      if newer needed → download once → re-exec from cache
         ↓
      go version / go test / go build / go run (same mechanism)
```

- **Bootstrap Go** — the `go` on your PATH. Entry point only.
- **Effective toolchain** — what actually compiles code (may be downloaded).
- **Compiled binary** — self-contained. No Go install needed at runtime.

---

## Key files & paths

| What | Where |
|------|--------|
| Bootstrap install | `/usr/local/go` (typical) |
| Downloaded toolchains | `$GOMODCACHE/golang.org/toolchain@v0.0.1-goVERSION.GOOS-GOARCH` |
| Module cache | `$GOMODCACHE` (default `$GOPATH/pkg/mod`) |
| Build cache | `$GOCACHE` (default `~/.cache/go-build`) |
| Persisted Go settings | `~/.config/go/env` (`go env -w`) |
| Project minimum Go | `go.mod` → `go 1.26.5` |
| Preferred toolchain | `go.mod` → `toolchain go1.26.5` (optional) |

Example downloaded path:

```
~/go/pkg/mod/golang.org/toolchain@v0.0.1-go1.26.5.linux-amd64/
├── bin/go
├── pkg/tool/...    ← compile, link, etc.
└── src/...
```

---

## go.mod lines

| Line | Meaning |
|------|---------|
| `go 1.26.5` | **Minimum** Go required (mandatory since Go 1.21) |
| `toolchain go1.26.5` | **Preferred** toolchain when working in this module |

Rules:

- Go **never auto-downloads an older** version.
- If bootstrap ≥ `go` line → use bootstrap (e.g. bootstrap 1.26.2, mod says 1.24.13).
- If bootstrap < `go` line → download/switch (e.g. bootstrap 1.26.2, mod says 1.26.5).

---

## GOTOOLCHAIN values

| Value | Behavior |
|-------|----------|
| `auto` (default) | `local+auto` — start with bootstrap, switch newer if mod requires |
| `local` | Always bootstrap; **fail** if project needs newer Go |
| `go1.26.5` | Always use that exact toolchain (PATH lookup, else download) |
| `go1.26.3+auto` | Default to 1.26.3, but switch newer if mod requires |
| `path` | `local+path` — switch via PATH only, **no download** |

Inspect: `go env GOTOOLCHAIN`

Persist: `go env -w GOTOOLCHAIN=auto`

---

## Why `go version` differs by folder

`go version` uses the **same toolchain selection** as `go test`.

| Directory | Typical output |
|-----------|----------------|
| No `go.mod` (e.g. `/tmp`) | Bootstrap version |
| `go 1.24.13` project, bootstrap 1.26.2 | `go1.26.2` (new enough) |
| `go 1.26.5` project, bootstrap 1.26.2 | `go1.26.5` (auto-switch) |

Useful commands:

```bash
go version                          # effective toolchain here
go env GOVERSION GOROOT             # version + tree in use
GOTOOLCHAIN=local go version        # bootstrap only
GOTOOLCHAIN=go1.26.5 go version     # force specific version
go version -m ./app                 # version baked into a binary
GODEBUG=toolchaintrace=1 go version # trace selection (Go 1.24+)
```

---

## What downloads Go vs what doesn't

| Command / action | Downloads Go compiler? |
|------------------|------------------------|
| `go test`, `go build`, `go run` | Yes, if bootstrap too old and `GOTOOLCHAIN=auto` |
| `go version` (in module dir) | Same selection logic (may switch) |
| `go mod tidy` | **No** — tidies modules; may update `go` line to version **you're running** |
| `go get some/pkg@v1` | **No** — updates dependency, not Go itself |
| `go get go@1.26.5` | Updates `go` line; uses running toolchain to do so |
| Running `./app` in production | **Never** |

Download happens **once per version**, then cached.

---

## Important env vars

### Use daily

| Var | Purpose |
|-----|---------|
| `GOPATH` | Module cache root, `go install` bin dir (`$GOPATH/bin`) |
| `GOPRIVATE` | Private module paths — skip proxy & sumdb |
| `GOTOOLCHAIN` | Toolchain selection (`auto` by default) |

### Usually leave alone

| Var | Notes |
|-----|-------|
| `GOROOT` | **Do not pin in `.bashrc`** — Go sets this per invocation; pinning causes version mismatches |
| `GOMODCACHE` | Where modules (and toolchains) are stored |
| `GOCACHE` | Build cache — `go clean -cache` after Go upgrades |

### Private modules (Artemis pattern)

```bash
export GOPRIVATE=dev.azure.com/slb-digital,dev.azure.com/slb-swt,slb-swt.visualstudio.com
# Often also set GONOPROXY / GONOSUMDB to same value
```

### Cross-compilation (CI / Docker)

```bash
CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -o app cmd/main.go
```

---

## Recommended ~/.bashrc

```bash
export GOPRIVATE=dev.azure.com/slb-digital,dev.azure.com/slb-swt,slb-swt.visualstudio.com
export GOPATH=$HOME/go
export PATH=/usr/local/go/bin:$GOPATH/bin:$PATH

# Do NOT set GOROOT — breaks toolchain switching
# GOTOOLCHAIN=auto is the default; only set if you need local-only mode
```

After removing `GOROOT` or upgrading Go:

```bash
go clean -cache
```

---

## Build time vs run time

| Build time (dev laptop / Docker builder stage) | Run time (pod / `./app`) |
|------------------------------------------------|--------------------------|
| Go compiler, `go.mod`, modules | Compiled binary only |
| `GOTOOLCHAIN`, toolchain cache | Go runtime **inside** the binary |
| Network for deps / toolchain download | Config, env vars, external services (Mongo, etc.) |

Docker pattern (this repo):

```
builder:  FROM golang:1.26.5  → go build
runtime:  FROM alpine         → COPY app; ENTRYPOINT ./app
```

---

## Common errors

### `compile: version "go1.26.2" does not match go tool version "go1.26.5"`

**Cause:** `GOROOT` pinned to old install while `go` driver is newer.

**Fix:** Remove `export GOROOT=...` from shell config; `go clean -cache`.

### `go.mod requires go >= 1.26.5 (running go 1.26.2; GOTOOLCHAIN=local)`

**Cause:** `GOTOOLCHAIN=local` disables auto-download.

**Fix:** Use default `auto`, or upgrade bootstrap, or `GOTOOLCHAIN=go1.26.5`.

---

## Hands-on drill (5 min)

```bash
cd /tmp && go version
cd ~/src/artemis/digital-twin-analysis-service && go version && go env GOROOT
cd ~/src/artemis/common-go && go version
ls ~/go/pkg/mod/golang.org/toolchain@*
GOTOOLCHAIN=local go version        # from any 1.26.5 project
GODEBUG=toolchaintrace=1 go version # from inside a module
```

---

## Further reading

| Topic | Link / command |
|-------|----------------|
| **Primary** — toolchains | https://go.dev/doc/toolchain |
| All env vars | `go help environment` |
| Module env vars | https://go.dev/ref/mod#environment-variables |
| Go 1.21 introduced this | https://go.dev/doc/go1.21#tools |
| Persist settings | `go help env` |
| Runtime GODEBUG | https://go.dev/doc/godebug |

---

## One-liners

- **PATH picks bootstrap; Go picks compiler internally.**
- **`go mod tidy` fixes dependencies, not your Go install.**
- **Never pin `GOROOT` in `.bashrc`.**
- **Production runs the binary, not `go`.**
