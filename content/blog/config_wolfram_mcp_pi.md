+++
date = '2026-08-27T10:41:15-04:00'
draft = false
title = 'Configure Wolfram_MCP for pi.dev'
description = "How to reuse Claude Desktop Wolfram MCP configuration in pi.dev"
tags = ["AI", "Wolfram", "pi.dev", "Tips"]
+++

### Wolfram Local MCP
Since Wolfram (or Mathematica) 15.0, it supports [Wolfram Local MCP](https://www.wolfram.com/artificial-intelligence/mcp/local/) out of the box. I have already let Wolfram configured the MCP server for Claude desktop, so we can reuse the configuration file for pi.dev.

![Wolfram AI Configuration](/images/blog/wolfram_ai_config.jpg "Wolfram AI Configuration")

**Note**: the following steps can be done by AI directly in pi.dev, no need to do it manually.  

### 1. MCP in pi.dev
pi.dev doesn't include MCP extensions, the first thing to do is to install the mcp extension if neccessary.
```bash
# persistent (recommended) — writes to ~/.pi/agent/settings.json
pi install npm:pi-mcp-extension

# verify
pi list
# should show: npm:pi-mcp-extension
```

### 2. Create pi MCP Config file
Copy the Wolfram configuration from Cloud desktop, on Mac, it is usually at this location: ~/Library/Application\ Support/Claude/claude_desktop_config.json.

Then create '~/pi/agent/mcp.json'.
Paste the code copied from Claude, it is necessary to do some extra editing, the new file shall be look at this:
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
**transport**:  `"stdio"`   
**lifecycle**: `"eager"` (auto-start) or `"lazy"` (manual `/mcp:start`) |

As a casual Mathematica user, the lifecycle is set as "lazy" rather than "eager".

### 3. Verify
Inside `pi`: 

```
/mcp:start Wolfram
Caculate the integral of x^2 + Sin(x) using Wolfram
/mcp:stop Wolfram
```
You shall be able to see the output from Wolfram, the result is "Pi^2 - 4".
