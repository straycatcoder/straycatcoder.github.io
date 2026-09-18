+++
title = 'Create a Skill with Wolfram Cloud MCP'
date = '2026-09-18T09:12:24-04:00'
draft = false
description = "Create a wolfram-plot skill with Wolfram cloud mcp."
tags = ["Wolfram", "AI","Ghostty", "Pi.dev"]
+++

In [the post on Wolfram Cloud MCP]({{< ref "test_cloud_wolfram_mcp_pi_ghostty.md" >}}), we are using the following prompt to create and display the plot in Ghostty.

> Use the Wolfram to generate a plot of Plot[Sin[x], {x, 0, 10}]. Take the resulting output URL or image payload and display it inline using your image-view tool.

Clearly, it is too tedious to write a prompt this long every time, and we can create a skill to simplify it. A skill is essentially a series instruction for AI agents to perform multiple-step workflow. 

With the skill, the prompt can be done in this simple way:
> /skill:wolfram-plot sin[xy] {x, -pi, pi}, {y, -pi, pi}

The AI agent will first sent the request to Wolfram Cloud MCP to generate the plot, then in the next step, find out the image url, finally pull the image and display it.

![an example of Wolfram plot skill](/images/blog/wolfram_plot_skill.png "an example of Wolfram plot skill")

The skill is at this location (global skills folders): `.agents/skills/wolfram_plot/SKILL.md`.

Here is the complete skill file:

````markdown
---
name: wolfram-plot
description: Generate Wolfram Language plots through the Wolfram MCP tools and display the resulting image inline. Use when the user asks for a Wolfram plot, WL Plot/ListPlot/ParametricPlot/etc., or says wolfram_plot.
---

# Wolfram Plot

Use this skill to turn a short request such as `wolfram_plot Plot[Sin[x], {x, 0, 10}]` into an inline plot image.

## Workflow

1. Call `mcp_wolfram_WolframContext` first with a natural-language summary of the requested plot.
2. Call `mcp_wolfram_WolframLanguageEvaluator` with the exact Wolfram Language plot expression.
   - Example code: `Plot[Sin[x], {x, 0, 10}]`
   - If the evaluator returns a formatted markdown image/link, use that directly in the final answer.
   - If the evaluator returns an image payload like `[Image: image/png, base64 encoded]`, treat it as the generated plot result.
3. If an inline-displayable URL is needed, use the Wolfram context/alpha result to locate the one-line image URL for the same expression, then call `fetch_content` on that image URL so it is displayed inline by the image-view tool.
4. Final response should be short: include only the inline image markdown and, if helpful, one sentence identifying the expression.

## Display pattern

When a public image URL is available:

```markdown
![Wolfram plot](IMAGE_URL)
```

When the image-view tool has already displayed the fetched image, still include the markdown image if a URL exists.

## Examples

User can say any of:

- `wolfram_plot Plot[Sin[x], {x, 0, 10}]`
- `Plot Sin[x] from 0 to 10 with Wolfram`
- `/skill:wolfram-plot Plot[Sin[x], {x, 0, 10}]`

For the example, evaluate:

```wl
Plot[Sin[x], {x, 0, 10}]
```

Then fetch/display the resulting Wolfram image URL inline.
````

