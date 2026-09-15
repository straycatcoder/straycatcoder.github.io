+++
date = '2026-08-27T10:41:15-04:00'
draft = false
title = 'Configure Local Wolfram MCP for pi.dev'
description = "Reuse your Claude Desktop Wolfram MCP config in pi.dev: install the MCP extension, add transport and lifecycle, then verify."
tags = ["AI", "Wolfram", "pi.dev", "Tips"]
+++

### Wolfram Local MCP

Since Wolfram (or Mathematica) 15.0, [Wolfram Local MCP](https://www.wolfram.com/artificial-intelligence/mcp/local/) works out of the box. Wolfram had already configured the MCP server for my Claude Desktop, so I reused that configuration file for pi.dev.

<!--more-->

![Wolfram AI configuration dialog showing the local MCP server setup](/images/blog/wolfram_ai_config.jpg "Wolfram AI Configuration")

**Note**: the following steps can be done by AI directly in pi.dev, no need to do it manually.  

### 1. MCP in pi.dev

pi.dev doesn't include MCP extensions, so the first step is to install the MCP extension if necessary.
```bash
# persistent (recommended) — writes to ~/.pi/agent/settings.json
pi install npm:pi-mcp-extension

# verify
pi list
# should show: npm:pi-mcp-extension
```

### 2. Create pi MCP Config file
Copy the Wolfram configuration from Claude Desktop. On a Mac, it usually lives at `~/Library/Application Support/Claude/claude_desktop_config.json`.

Then create `~/pi/agent/mcp.json`.
Paste in the code copied from Claude with a little extra editing. The new file should look like this:
```json
{
  "mcpServers": {
    "Wolfram": {
      "transport": "stdio",
      "command": "/Applications/Wolfram.app/Contents/MacOS/wolfram",
      "args": [
        "-run",
        "PacletSymbol[\"Wolfram/AgentTools\",\"Wolfram`AgentTools`StartMCPServer\"][]",
        "-noinit",
        "-noprompt"
      ],
      "env": {
        "MCP_SERVER_NAME": "Wolfram",
        "WOLFRAM_BASE": "/Library/Wolfram",
        "WOLFRAM_USERBASE": "/Users/username/Library/Wolfram",
        "WOLFRAM_LOCALBASE": "/Users/username/Library/Wolfram/Objects"
      },
      "lifecycle": "lazy"
    }
  }
}
```

There are two new fields:

- **transport**: `"stdio"`
- **lifecycle**: `"eager"` (auto-start) or `"lazy"` (manual `/mcp:start`)

As a casual Mathematica user, I set the lifecycle to `"lazy"` rather than `"eager".

### 3. Verify
Inside `pi`: 

```
/mcp:start Wolfram
Caculate the integral of x^2 + Sin(x) using Wolfram
/mcp:stop Wolfram
```
You should see output from Wolfram — the result is `Pi^2 - 4`.
