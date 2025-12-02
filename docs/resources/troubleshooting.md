# Troubleshooting

Common issues and their solutions.

## Installation Issues

### "Command not found: opencode"

**Problem**: The OpenCode CLI is not installed or not in your PATH

**Solution**:

The OpenCode CLI is not installed. Install it first:

```bash
npm install -g opencode-ai@latest
```

After installation, verify it works:

```bash
opencode --version
```

If you still get "command not found", restart your terminal or add npm global bin to your PATH.

### Windows NPX Installation Issues

**Problem**: `error: unknown option '-y'` when using Claude Code on Windows

**Solution**: Use one of these alternative installation methods:

```bash
# Method 1: Install globally first
npm install -g @gilby125/opencode-mcp-tool
claude mcp add opencode -- opencode-mcp

# Method 2: Use --yes instead of -y
claude mcp add opencode -- npx --yes @gilby125/opencode-mcp-tool

# Method 3: Remove the -y flag entirely
claude mcp add opencode -- npx @gilby125/opencode-mcp-tool
```

### "MCP server not responding"

**Problem**: Claude Desktop can't connect to the MCP server

**Step-by-step solution**:

1. **Check your Claude Desktop config file location**
   - macOS: `~/Library/Application Support/Claude/claude_desktop_config.json`
   - Windows: `%APPDATA%\Claude\claude_desktop_config.json`

2. **Verify JSON syntax is correct**
   - Use a JSON validator online
   - Check for missing commas, brackets, or quotes

3. **Restart Claude Desktop completely**
   - Quit completely (Cmd+Q on Mac)
   - Wait 5 seconds
   - Restart Claude Desktop

4. **Check logs for detailed errors**
   - macOS: `~/Library/Logs/Claude/`
   - Windows: `%APPDATA%\Claude\logs\`

### "MCP error -32000: Connection closed"

**Problem**: Server fails to start and connection closes immediately (Claude Code)

**Common causes**:

1. **Node.js version compatibility** - Ensure Node.js ≥ v16.0.0
2. **OpenCode CLI not installed** - Install with `npm install -g @google/opencode`
3. **API key not configured** - Run `opencode config set api_key YOUR_API_KEY`
4. **PATH issues** - Restart terminal after installing Node.js/npm

**Debug steps**:

```bash
# 1. Check Node.js version
node --version

# 2. Test OpenCode CLI directly
opencode "Hello"

# 3. Reinstall if needed
npm uninstall -g @gilby125/opencode-mcp-tool
npm install -g @gilby125/opencode-mcp-tool

# 4. Verify Claude Code can find the command
claude mcp list
```

**Still not working?** Check the Claude Desktop logs for detailed error messages:

- macOS: `~/Library/Logs/Claude/`
- Windows: `%APPDATA%\Claude\logs\`

### "OpenCode gets cut off" / Early Termination

**Problem**: Responses appear truncated or Claude reports "OpenCode was thinking but got cut off"

**Causes**:

- Large codebase analysis taking longer than expected
- Complex operations requiring extended processing time
- Client connection management issues

**Solutions**:

```bash
# The tool automatically prevents timeouts with progress updates.
# You'll see messages like:
# "Starting analysis (may take 5-15 minutes for large codebases)."
# "Gemini is analyzing your request..."

# Use a faster model for large requests
/opencode:plan -m <model> @large-file.js

# Break up large analysis into smaller chunks
/opencode:plan @specific-function.js explain this function
```

## Configuration Issues

### Changes not taking effect

1. Save config file
2. Completely quit Claude Desktop
3. Restart Claude Desktop
4. Verify with `/opencode:help`

### Configurable Timeout for Large Codebases

**Problem**: Default MCP client timeout too short for large analysis

**Root Cause**: Claude Desktop/Claude Code has a hard-coded timeout that cannot be overridden by environment variables.

**Solution**: The tool now automatically sends progress updates to prevent timeouts

```bash
# The tool will automatically send progress messages like:
# "Starting analysis (may take 5-15 minutes for large codebases)."
# "OpenCode is analyzing your request..."
# "Processing files and generating insights..."
# "Still processing... OpenCode is working on your request."
```

**What happens during long operations**:

- Progress updates every 25 seconds during active processing
- Backup heartbeat every 20 seconds to ensure connection stays alive
- Clear status messages showing the tool is working
- Automatic completion notification when done

**For very large codebases** (10,000+ files):

- Consider breaking analysis into smaller chunks
- Use more specific file patterns with `@` syntax
- Switch to `gemini-2.5-flash` for faster processing

````

## Debug Mode

Enable debug logging:
```json
{
  "mcpServers": {
    "opencode": {
      "command": "opencode-mcp",
      "env": {
        "DEBUG": "true"
      }
    }
  }
}
````

## Getting Help

1. Check GitHub issues for this repository
2. Enable debug mode
3. Collect error logs
4. Open a new issue with details

## Quick Fixes

### Reset Everything

```bash
# Remove and reinstall
npm uninstall -g @gilby125/opencode-mcp-tool
npm install -g @gilby125/opencode-mcp-tool

# Reset OpenCode CLI
opencode config reset
opencode config set api_key YOUR_API_KEY
```

### Test Basic Functionality

```bash
# Test OpenCode CLI
opencode "Hello"

# Test MCP Tool
/opencode:ping

# Test file analysis with working model
/opencode:plan -m <model> @README.md summarize
```

## Platform-Specific Issues

### Windows 11

- **NPX flag issues**: Use `--yes` instead of `-y`
- **Path problems**: Restart terminal after Node.js installation
- **Connection issues**: Ensure Windows Defender isn't blocking Node.js

### macOS

- **Permission issues**: Use `sudo` if npm install fails
- **Terminal restart**: Required after installing dependencies

### Linux

- **Node.js version**: Install via NodeSource for latest version
- **npm permissions**: Configure npm to avoid sudo usage
