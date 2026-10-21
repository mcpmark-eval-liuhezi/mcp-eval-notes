# PR review: most recently updated open PR

The most recently updated **open** pull request in `modelcontextprotocol/servers` as of this research (2026-10-21).

| Field | Value |
| --- | --- |
| PR number | #4551 |
| Title | `feat(everything): serve both protocol eras on SDK v2 (2026-07-28 + legacy)` |
| Author | `olaservo` |
| State | Open |
| Files changed | 54 |
| Additions | 2,266 |
| Deletions | 2,510 |

URL: https://github.com/modelcontextprotocol/servers/pull/4551

Head SHA at time of review: `b6fe776e5084f992f2bceadf0dfc7d416cac73b9`

## Where the changes land

- `src/everything/transports/*` — stdio, SSE and Streamable HTTP entries rewired to the new SDK serving entries
- `src/everything/server/*` — server factory, notifier routing, HMAC `requestState` codec
- `src/everything/tools/*` — every tool migrated; two removed, one added
- `src/everything/docs/*` + README — architecture/feature docs rewritten for the dual-era design
- `package-lock.json` / `package.json` — dependency swap to the v2 SDK packages

## Plain-English summary

This PR migrates the `everything` reference server from the v1 TypeScript SDK (`@modelcontextprotocol/sdk`) to the new v2 SDK packages, and in doing so makes it "dual-era": a single codebase that serves both the legacy MCP protocol revisions (2024-10-07 through 2025-11-25, negotiated via the `initialize` handshake) and the new modern revision 2026-07-28 (negotiated via a `server/discover` probe). Because the modern revision removed the `initialize` handshake, sessions, the server-to-client request channel, and SSE resumability, the PR reworks how tools get input from the client — instead of pushing a server-to-client request, they now return `inputRequired(...)`, which the SDK's legacy shim converts back into a real request for legacy clients, so no tool has to branch on `ctx.era`. It also deletes two tools that cannot exist on the modern era (the async sampling and elicitation tools, ~500 lines, built on the now-removed experimental tasks layer), rewrites `simulate-research-query` as an ordinary multi-round-trip tool using an HMAC-sealed `requestState`, and adds a new `get-structured-content-list` tool demonstrating the array-rooted `outputSchema` that the 2026-07-28 revision newly permits. Tools now register unconditionally rather than being capability-gated (the SDK refuses a caller lacking a capability at dispatch with `-32021`), the Streamable HTTP transport drops its session map and event store (238 → ~90 lines), and tests and docs are updated throughout — 112 vitest tests passing on both eras.
