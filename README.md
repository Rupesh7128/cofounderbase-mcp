# Cofounderbase MCP server

Search **960+ evidence-checked AI automation agencies** (n8n, Make, Zapier, Retool, voice agents, chatbots, RAG, internal tools) by need, tool, country and budget, from any MCP client.

- **Endpoint (Streamable HTTP, no auth, free):** `https://cofounderbase.com/api/mcp/`
- **Docs & live demo:** https://cofounderbase.com/mcp/
- **Official MCP Registry:** `io.github.Rupesh7128/cofounderbase`

This is a hosted (remote) server. There is nothing to install or run locally; this repo holds the metadata and install instructions.

## One-click install

[![Add to Cursor](https://cursor.com/deeplink/mcp-install-dark.svg)](https://cursor.com/en/install-mcp?name=cofounderbase&config=eyJ1cmwiOiJodHRwczovL2NvZm91bmRlcmJhc2UuY29tL2FwaS9tY3AvIn0=)
[![Install in VS Code](https://img.shields.io/badge/VS_Code-Install_Server-0098FF?logo=visualstudiocode)](https://insiders.vscode.dev/redirect/mcp/install?name=cofounderbase&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A//cofounderbase.com/api/mcp/%22%7D)

## Install

**Claude (web/desktop):** Settings → Connectors → *Add custom connector* → name `Cofounderbase`, URL `https://cofounderbase.com/api/mcp/`, no auth.

**ChatGPT:** Settings → Apps & Connectors → Advanced → enable *Developer mode*, then *Create* → MCP server URL `https://cofounderbase.com/api/mcp/`, Authentication: *No authentication*.

**Claude Code:**
```bash
claude mcp add --transport http cofounderbase https://cofounderbase.com/api/mcp/
```

**Cursor** (`~/.cursor/mcp.json`):
```json
{ "mcpServers": { "cofounderbase": { "url": "https://cofounderbase.com/api/mcp/" } } }
```

**VS Code:**
```bash
code --add-mcp '{"name":"cofounderbase","type":"http","url":"https://cofounderbase.com/api/mcp/"}'
```

**stdio-only clients:** `npx -y mcp-remote https://cofounderbase.com/api/mcp/`

## Tools

| Tool | What it does |
|---|---|
| `search_agencies` | Ranked agencies for a plain-English need; optional `country`, `tool`, `budget` filters |
| `get_agency` | Full profile: location, tools, use cases, prices, case studies, score |
| `top_agencies` | Highest-scored agencies for a use case, tool or country |
| `request_intro` | Asks Cofounderbase to introduce the user to up to 5 agencies (only on explicit request with the user's email) |

Example prompt: *"Find n8n agencies in the UK that build voice agents under $5k."*

## Test

```bash
curl -s https://cofounderbase.com/api/mcp/ -H 'content-type: application/json' \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"top_agencies","arguments":{"category":"Voice agents","limit":3}}}'
```

## License
MIT (this repo's docs/metadata). Data © Cofounderbase.
