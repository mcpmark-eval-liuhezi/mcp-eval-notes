# Latest release

The most recent release of `modelcontextprotocol/servers` as of this research.

| Field | Value |
| --- | --- |
| Tag | `v2.0.0` |
| Release title | v2.0.0 |
| Published by | `cliffhall` (Cliff Hall) |
| Published at | 2026-10-19T06:46:50Z (2026-10-19 06:46:50 UTC) |

## Summary of the release notes

Release v2.0.0 refactors the servers to support the "modern era" of the MCP specification (protocol revision 2026-07-28) while still responding to legacy-era clients as expected, and it publishes seven updated packages: the four TypeScript servers (`@modelcontextprotocol/server-everything`, `-filesystem`, `-memory`, `-sequential-thinking`) at version 2.0.0 on npm, and the three Python servers (`mcp-server-fetch`, `mcp-server-git`, `mcp-server-time`) at `2026.10.19` on PyPI. For clients, the release notes call out some behavior changes in the Python servers — e.g. unknown tools now return a JSON-RPC `-32602` error as the spec requires (previously an `isError` result), and tool error messages now read `Error executing tool <name>: <message>` — because those servers were rebuilt on the MCP Python SDK's high-level `MCPServer` (PR #5175).
