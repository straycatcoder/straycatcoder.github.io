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
