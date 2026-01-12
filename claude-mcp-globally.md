Goal: Configure Notion MCP server globally (not per-project)

Solution: Add mcpServers to ~/.claude.json (not ~/.claude/mcp.json)

```
  {
    "mcpServers": {
      "notion": {
        "command": "npx",
        "args": ["-y", "@notionhq/notion-mcp-server"],
        "env": {
          "NOTION_API_KEY": "your-api-key"
        }
      }
    },
    // ... rest of config
  }
```

Key learnings:
  - ~/.claude/mcp.json does not work for global MCP config
  - Global MCP servers go in ~/.claude.json under the root mcpServers key
  - Project-level .mcp.json files override/supplement global config
  - Environment variable must be NOTION_API_KEY (not NOTION_TOKEN)

Useful commands:
  - claude mcp list - verify configured servers
  - claude mcp add --scope user - add global servers via CLI
