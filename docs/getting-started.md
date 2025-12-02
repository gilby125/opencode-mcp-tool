# Getting Started

## Client Options

### Claude Code (Recommended)
**Power Users** - One-command setup  
[Get Started →](#claude-code-recommended)

### Claude Desktop  
**Everyday users** - JSON configuration  
[Setup Guide →](#claude-desktop)

### Other Clients
Multiple options including Warp, Copilot, and others  
[More →](#other-mcp-clients)

## Client Setup

## Prerequisites

Before installing, ensure you have:

- **[Node.js](https://nodejs.org/)** v16.0.0 or higher
- **[OpenCode CLI](https://github.com/fictiverse/opencode)** installed and configured on your system
- **[Claude Desktop](https://claude.ai/download)** or **[Claude Code](https://www.anthropic.com/claude-code)** with MCP support


## Claude Code (Recommended)

**Note:** opencode-mcp-tool is tested extensively with Claude Code.

Claude Code offers the smoothest experience.

```bash
# install for claude code
claude mcp add opencode -- npx -y opencode-mcp-tool

# Start Claude Code - it's automatically configured!
claude
```

## Claude Desktop
---
#### Configuration File Locations

**Where are my Claude Desktop Config Files?**

- **macOS**: `~/Library/Application Support/Claude/claude_desktop_config.json`
- **Windows**: `%APPDATA%\Claude\claude_desktop_config.json`
- **Linux**: `~/.config/claude/claude_desktop_config.json`

---

For Claude Desktop users, add this to your configuration file:

```json
{
  "mcpServers": {
    "opencode": {
      "command": "npx",
      "args": ["-y", "opencode-mcp-tool"]
    }
  }
}
```

**Important:** You must restart Claude Desktop completely for changes to take effect.
## Other MCP Clients

OpenCode MCP Tool works with 40+ MCP clients! Here are the common configuration patterns:

### STDIO Transport (Most Common)
```json
{
  "transport": {
    "type": "stdio",
    "command": "npx",
    "args": ["-y", "opencode-mcp-tool"]
  }
}
```

### Popular Clients

<details>
<summary><strong>Warp</strong> - Modern terminal with AI features</summary>

**Configuration Location:** Terminal Settings → AI Settings → MCP Configuration

```json
{
  "opencode": {
    "command": "npx",
    "args": [
      "-y",
      "opencode-mcp-tool"
    ],
    "env": {},
    "working_directory": null,
    "start_on_launch": true
  }
}
```

**Features:** Terminal-native MCP integration, AI-powered command suggestions
</details>

<details>
<summary><strong>Codex CLI</strong> - OpenAI terminal assistant with MCP support</summary>

**Quick setup (recommended):**

```bash
codex mcp add opencode -- npx -y opencode-mcp-tool -- --model google/gemini-2.5-pro --fallback-model google/gemini-2.5-flash
```

This registers `opencode` as an MCP server using stdio transport. Once added, start Codex CLI normally and use natural language like:

- "use opencode to analyze @src/main.ts"
- "ask opencode to summarize @. the current directory"
</details>
### Generic Setup Steps

1. **Install Prerequisites**: Ensure [OpenCode CLI](https://github.com/fictiverse/opencode) is installed
2. **Add Server Config**: Use the STDIO transport pattern above
3. **Restart Client**: Most clients require restart after config changes
4. **Test Connection**: Try `/opencode:ping` or natural language commands

## Verify Your Setup

Once configured, test that everything is working:

### 1. Basic Connectivity Test
Type in Claude:
```
/opencode:ping "Hello from OpenCode MCP!"
```

### 2. Test File Analysis
```
/opencode:plan @README.md summarize this file
```

### 3. Test Plan Mode
```
/opencode:plan create a simple Python hello world script
```

## Quick Command Reference

Once installed, you can use natural language or slash commands:

### Natural Language Examples
- "use opencode to explain index.html"
- "understand the massive project using opencode"
- "ask opencode to search for latest news"

### Slash Commands in Claude Code
Type `/opencode` and these commands will appear:
- `/opencode:plan` - Structured analysis and planning (default mode)
- `/opencode:build` - Immediate code execution
- `/opencode:help` - Show help information
- `/opencode:ping` - Test connectivity

## Need a Different Client?

Don't see your MCP client listed? OpenCode MCP Tool uses standard MCP protocol and works with any compatible client.

**Find More MCP Clients:**
- **Official List**: [modelcontextprotocol.io/clients](https://modelcontextprotocol.io/clients)
- **Configuration Help**: Most clients follow the STDIO transport pattern above
- **Community**: Join discussions on GitHub for client-specific tips

## Common Issues

### "Command not found: opencode"
Make sure you've installed the OpenCode CLI:
```bash
npm install -g opencode
```

### "MCP server not responding"
0. Run Claude Code and use `/doctor`
1. Check your configuration file path
2. Ensure JSON syntax is correct
3. Restart your MCP client completely
4. Verify OpenCode CLI works: `opencode -help`


### Client-Specific Issues
- **Claude Desktop**: Must restart completely after config changes
- **Other Clients**: Check their specific documentation for MCP setup

## Next Steps

Now that you're set up:
- Learn about file analysis with @ syntax
- Explore plan mode for structured development
- Use build mode for immediate execution
- Check out real-world examples in the README

**Need Help?** If you run into issues, open a GitHub issue in the main repository.
