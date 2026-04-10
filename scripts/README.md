# scripts/

Build, provisioning, and diagnostic scripts. All run via `bun run ...`.

## Files

- `build.ts` — Bun bundler entrypoint. Produces `dist/cli.mjs`, inlines
  `MACRO.*` constants, flips internal feature flags off.
- `no-telemetry-plugin.ts` — Bun plugin that strips telemetry / analytics
  imports from the bundle.
- `provider-bootstrap.ts` — Writes `.openclaude-profile.json` for a chosen
  provider (`profile:init`).
- `provider-discovery.ts` — Probes the local environment for usable
  providers (Ollama, OpenAI key, Codex, Atomic Chat).
- `provider-recommend.ts` — Recommends a provider/model based on goal
  (`latency`, `balanced`, `coding`).
- `provider-launch.ts` — Launches the CLI with a prepared profile
  (`dev:profile`, `dev:ollama`, etc.).
- `system-check.ts` — Runtime doctor. Human-readable and `--json` modes,
  plus `--out` for report artifacts (`doctor:runtime`, `doctor:report`).

## Common entrypoints

```bash
bun run build            # scripts/build.ts
bun run dev:profile      # scripts/provider-launch.ts
bun run profile:init     # scripts/provider-bootstrap.ts
bun run doctor:runtime   # scripts/system-check.ts
```
