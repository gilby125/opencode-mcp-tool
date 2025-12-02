# Installation

Multiple ways to install OpenCode MCP Tool, depending on your needs.

## Prerequisites

- Node.js v16.0.0 or higher
- Claude Desktop or Claude Code with MCP support
- OpenCode CLI installed (`npm install -g opencode`)

## Method 1: NPX (Recommended)

No installation needed - runs directly:

```json
{
  "mcpServers": {
    "opencode": {
      "command": "npx",
      "args": ["-y", "@gilby125/opencode-mcp-tool"]
    }
  }
}
```

## Method 2: Global Installation

```bash
claude mcp add opencode -- npx -y @gilby125/opencode-mcp-tool
```

Then configure:
```json
{
  "mcpServers": {
    "opencode": {
      "command": "opencode-mcp"
    }
  }
}
```

## Method 3: Local Project

Use GitHub Packages or npm with the scoped name: `@gilby125/opencode-mcp-tool`.

See [Getting Started](/getting-started) for full setup instructions.
