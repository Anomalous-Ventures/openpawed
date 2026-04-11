# bin/

Executable entrypoints shipped in the npm package.

## Files

- `openclaude` — Node shim invoked by the `openclaude` global command. Loads
  `dist/cli.mjs` if built, otherwise prints build instructions.
- `import-specifier.mjs` — Small helper for resolving import specifiers at
  runtime (used by the bundle loader).
- `import-specifier.test.mjs` — Unit test for the resolver, runnable with
  `node --test bin/import-specifier.test.mjs`.

## Usage

After `npm install -g @gitlawb/openclaude` the `openclaude` binary in this
directory becomes the global command. For local development run
`bun run build` first to populate `dist/cli.mjs`.
