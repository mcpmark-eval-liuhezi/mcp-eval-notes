# Overview

This note captures the most-starred GitHub repository implementing the Model Context Protocol (MCP), found by live search on GitHub.

## Repository facts

| Field | Value |
| --- | --- |
| Full name | `modelcontextprotocol/servers` |
| Star count | 91,446 |
| Default branch | `main` |
| Language | TypeScript |
| Forks | 11,837 |
| Open issues/PRs | 139 |
| Homepage | https://modelcontextprotocol.io |
| Created | 2024-11-19 |

## What the project is

`modelcontextprotocol/servers` is the official collection of reference MCP server implementations published by the Model Context Protocol organization (the body that maintains the MCP standard). MCP is an open standard, introduced by Anthropic in November 2024, for connecting AI applications to external data sources and tools through a client-server architecture, and this repository is where the canonical, spec-conformant server implementations live. The TypeScript servers it ships are published to npm as scoped packages (`@modelcontextprotocol/server-everything`, `-filesystem`, `-memory`, `-sequential-thinking`) and the Python servers (`mcp-server-fetch`, `mcp-server-git`, `mcp-server-time`) are published to PyPI. The `everything` server in particular is not meant to be useful on its own; it deliberately exercises nearly every feature of the MCP spec (tools, prompts, resources, sampling, elicitation, roots, logging, subscriptions) so that builders of MCP *clients* have a conformance target to test against. With ~91.4k stars and ~11.8k forks it is by far the most-starred MCP implementation on GitHub, roughly 4x the next one (`modelcontextprotocol/python-sdk`, ~24.6k stars), and it is the primary reference point for anyone evaluating the maturity of the MCP ecosystem.
