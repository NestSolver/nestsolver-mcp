# NestSolver MCP server

Plan cutting and loading jobs from a plain request in your AI assistant.
NestSolver's hosted MCP server gives any MCP client the same planner as
[nestsolver.com](https://nestsolver.com): cut lists for bars and sheets,
true-shape nests of parts from DXF, DWG or SVG drawings, and pallet and
truck loads with stacking rules and axle checks.

- **Server:** `https://mcp.nestsolver.com` (Streamable HTTP)
- **Sign-in:** OAuth 2.1. Connecting asks you to sign in to NestSolver and
  pick a workspace; there is no key to copy.
- **Registry:** `com.nestsolver/nestsolver` in the
  [MCP Registry](https://registry.modelcontextprotocol.io)

This repository holds no code: NestSolver hosts the server. It describes
the server for directories and for the people adding it to their clients.

## Connect

- **Claude:** add NestSolver from the
  [connector directory](https://claude.ai/directory/connectors/nestsolver).
- **Claude Code:** install the
  [NestSolver plugin](https://github.com/NestSolver/claude-plugin), or add
  the server on its own and sign in with `/mcp`:

  ```
  claude mcp add --transport http nestsolver https://mcp.nestsolver.com
  ```

- **VS Code:** add it to `.vscode/mcp.json`, then start it and sign in:

  ```json
  {
    "servers": {
      "nestsolver": { "type": "http", "url": "https://mcp.nestsolver.com" }
    }
  }
  ```

- **Cursor:** use **Add to Cursor** on
  [nestsolver.com/mcp](https://nestsolver.com/mcp), or add it to
  `~/.cursor/mcp.json` and sign in when Cursor asks:

  ```json
  {
    "mcpServers": {
      "nestsolver": { "url": "https://mcp.nestsolver.com" }
    }
  }
  ```

- **Other MCP clients:** add a remote (Streamable HTTP) server at
  `https://mcp.nestsolver.com` and sign in when asked.

## Tools

| Tool | What it does |
|---|---|
| `validate_linear` | Check a cut list of bars, pipe, tube, extrusion or lumber without solving it. |
| `solve_linear` | Cut parts from lengths of stock with the least waste: the bars used, each cut's place, the drops worth keeping. |
| `validate_sheet` | Check a cut list of rectangles from sheets without solving it. |
| `solve_sheet` | Cut rectangles from sheets for a panel saw or a CNC router: each sheet's parts, saw cuts and leftovers. |
| `start_nest` | Queue a true-shape nest of saved parts, or of rectangles and circles, on sheets. |
| `start_load` | Queue a load of cartons onto pallets, or of pallets into trucks and containers. |
| `get_job_status` | Tell where a nest or load stands. |
| `get_plan_report` | Read a finished nest or load: its figures, layouts, loading steps, axle checks and export links. |
| `get_usage` | Read this month's search time and what's left. |
| `list_parts` | List the workspace's saved parts for nesting. |
| `list_spaces` | List the workspace's saved cartons, pallets and vehicles. |

The checks, status, plan, usage and list tools only read. No tool deletes
anything or reaches past your workspace. The full reference is at
[docs.nestsolver.com/mcp-tools](https://docs.nestsolver.com/mcp-tools).

## What it needs

A NestSolver account, free to make. What each plan includes is on the
[pricing page](https://nestsolver.com/pricing).

NestSolver sees only the cut lists, parts and cargo sent through its tools,
never your conversation.

## Links

- Docs: https://docs.nestsolver.com/mcp
- Privacy: https://nestsolver.com/privacy
- Terms: https://nestsolver.com/terms
- Support: support@nestsolver.com
