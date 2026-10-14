# Installing TG Market MCP (for AI agents)

TG Market is a hosted remote MCP server. There is nothing to clone, build or run locally.

1. Ask the user for a TG Market API key (`mk_live_...`). They can create one after a free sign-up at https://tgmarket.io (account → API keys).
2. Add this server to the MCP settings file:

```json
{
  "mcpServers": {
    "tgmarket": {
      "type": "streamableHttp",
      "url": "https://tgmarket.io/mcp",
      "headers": { "Authorization": "Bearer mk_live_..." }
    }
  }
}
```

3. If the client cannot connect over HTTP, use the stdio bridge instead:

```json
{
  "mcpServers": {
    "tgmarket": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://tgmarket.io/mcp", "--header", "Authorization:${MK_AUTH}"],
      "env": { "MK_AUTH": "Bearer mk_live_..." }
    }
  }
}
```

4. Verify with `list_languages` or `get_usage` — both are free.
