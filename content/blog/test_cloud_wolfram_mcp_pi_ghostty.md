+++
title = 'Test Wolfram Cloud MCP with pi.dev'
date = '2026-09-17T11:05:20-04:00'
draft = false
description = "Test Cloud Wolfram MCP server in pi.dev with inline image support from Ghostty"
tags = ["Wolfram", "AI", "Ghostty","Pi.dev"]
+++
I have tested the local MCP server on Mac, and today I am testing [Wolfram Cloud MCP server](https://www.wolfram.com/artificial-intelligence/mcp/cloud/) in ChromeOS Flex, currently it free for the personal use.

To use MCP in pi.dev, install npm:pi-mcp-extension first.
Here is the minimum configuration for mcp.json.
```json
{
  "settings": {
    "toolPrefix": "mcp",
    "requestTimeoutMs": 30000,
    "maxRetries": 5
  },
  "mcpServers": {
    "wolfram": {
      "transport": "streamable-http",
      "url": "https://agenttools.wolfram.com/mcp",
      "lifecycle": "eager"
    }
  }
}
```

Ghostty terminal supports the Kitty graphics protocol to display inline images directly within the terminal, it will be nice if we can display the plots generated from the Wolfram Cloud.

To do this, we need to install: "pi install npm:pi-image-view", then let's have a try:

> Use the Wolfram to generate a plot of Plot[Sin[x], {x, 0, 10}]. Take the resulting output URL or image payload and display it inline using your image-view tool.


Here we go: 
![Display inline plot from Wolfram Cloud](/images/blog/wolfram_mcp_ghostty_plot.png "Display inline plot from Wolfram Cloud")

