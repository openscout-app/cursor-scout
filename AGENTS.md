# Scout for Cursor

This repository is the Cursor integration for Scout. It is public. It holds
the Cursor MCP configuration, an installer, and documentation that make Cursor
and `cursor-agent` start `scout mcp`.

## Where work goes

- The Scout MCP server is `scout mcp`, from the core. Do not implement Scout
  tools here. A thin wrapper is acceptable only when Cursor requires one.
- Behavior that every harness needs goes to the core repository,
  `openscout-app/scout`. Land it there first, then use it here.
- Behavior specific to Cursor goes here: the configuration, the installer,
  and Cursor guidance.

| Path | Holds |
| --- | --- |
| `.cursor/mcp.json` | Project-level Cursor configuration for local tests |
| `scripts/install.mjs` | Writes the `scout` entry into the global or project Cursor configuration |
| `scripts/install.test.mjs` | Installer tests |
| `docs/index.html` | The GitHub Pages site |

## Rules

- The installer must not replace a different `scout` entry unless the user
  passes `--force`. `--dry-run` must write nothing.
- Do not claim guaranteed distributed delivery.
- Scout is for high-trust local developer use. Do not claim enterprise,
  compliance, or multi-tenant readiness.
- This repository is public. Do not commit local paths, host names,
  credentials, or private source.

## Checks

- `bun run check`

## Commits and pull requests

- Commit subjects use gitmoji: `🐛 Keep the existing entry without --force`.
- Do not add AI co-author trailers or "Generated with" lines.
- Push a branch to `openscout-app/cursor-scout` and open a pull request into
  `main`.

<!-- scout:begin -->
## Scout

- Work for another agent, or on another machine, goes through Scout: `scout ask` (MCP `ask`).
- Another machine: `scout ask --on <host> --project <path on that host> --harness <claude|codex>`; `scout hosts` lists machines and their projects. Don't ssh in to launch agents.
- Syntax: `scout ask --help`, `scout help --detail`. Added by `scout setup agents-md`; `scout setup agents-md --remove` takes it out.
<!-- scout:end -->
