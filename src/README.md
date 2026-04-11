# src/

TypeScript source for the CLI agent. Bundled to `dist/cli.mjs` by
`scripts/build.ts`.

## Layout

- `entrypoints/` — Top-level CLI bootstrap and REPL wiring.
- `cli/` — Command parsing, handlers (`agents`, `auth`, etc.).
- `commands/` — Built-in slash commands (`/commit`, `/review`, `/compact`,
  `/diff`, `/doctor`, ...).
- `tools/` — Tool implementations. Bash, FileRead/Write/Edit, Glob, Grep,
  WebFetch, WebSearch, Agent, MCP, LSP, NotebookEdit, Task*, Worktree, etc.
- `services/` — Cross-cutting services:
  - `api/` — Provider clients, including the OpenAI-compatible shim
    (`openaiShim.ts`) and the Codex shim (`codexShim.ts`).
  - `mcp/`, `lsp/`, `oauth/`, `plugins/`, `github/`, `voice*`, ...
- `query/`, `tasks/`, `Task.ts`, `QueryEngine.ts` — Agent loop, task graph,
  and query engine.
- `screens/`, `components/`, `ink/`, `ink.ts` — React + Ink terminal UI.
- `bridge/` — Remote-bridge transport (feature-flagged off in open build).
- `remote/`, `server/` — Remote session support.
- `assistant/`, `buddy/` — Session chooser and companion UI.
- `keybindings/`, `vim/`, `outputStyles/` — Input and rendering config.
- `memdir/`, `migrations/`, `history.ts`, `SessionMemory` — Persistence.
- `coordinator/`, `upstreamproxy/`, `native-ts/` — Infra.
- `schemas/`, `types/`, `utils/`, `constants/`, `state/`, `hooks/` — Shared.
- `skills/` — Skill definitions and loader.
- `plugins/` — Plugin system.
- `tools.ts`, `commands.ts`, `context.ts`, `query.ts`, `Tool.ts` — Public
  barrels re-exporting the primary surfaces.

## Tests

Tests live next to their sources as `*.test.ts` and run with `bun test`.
See `package.json` scripts `test:provider` and `test:provider-recommendation`.
