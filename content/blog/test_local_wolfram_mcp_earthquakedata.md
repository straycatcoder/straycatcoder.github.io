+++
title = "Test Local Wolfram MCP II: EarthquakeData"
date = "2026-09-08T13:20:39-04:00"
draft = false
description = "Revisiting a 2017 EarthquakeData critique on Wolfram 15.0.1 with Claude, ChatGPT, and muse-spark — does the warning still hold?"
tags = ["AI","Wolfram", "ChatGPT", "Claude", "MetaAI"]
+++
**Note**: this is simply a test of the Wolfram MCP integration with AI — nothing more.

With the Wolfram MCP server, we can attempt something more complex than plain coding.

<!--more-->

There is an interesting 2017 post, ["Don't Study Large Earthquakes with Mathematica's EarthquakeData"](https://sites.psu.edu/charlesammon/2017/05/01/dont-study-large-earthquakes-with-mathematica/) by Charles J. Ammon.
Nine years later, on Wolfram Language 15.0.1, is it still the case? Let's revisit that post with AI.

I tested the claims in Claude and ChatGPT, and verified them with Meta's muse-spark model. I won't go into the details here — the reports are listed in the table below.

The conclusion: the main claim from Ammon's post in 2017 still holds on WL 15.0.1 today: if you need to work with earthquake magnitude data in Mathematica, import it from USGS, ISC, or GCMT directly rather than relying on EarthquakeData. 


| File | What it is |
|---|---|
| [`blogpost-followup-claude-sonnet-5.md`](https://github.com/straycatcoder/mathematica_learning/tree/main/blogs/earthquakedata/blogpost-followup-claude-sonnet-5.md) | Follow-up A (Claude): tight literal re-run of Ammon's 9 claims on WL 15.0.1, with `Wolfram vs reference` bar charts |
| [`blogpost-followup-GPT5.6-sol.md`](https://github.com/straycatcoder/mathematica_learning/tree/main/blogs/earthquakedata/blogpost-followup-GPT5.6-sol.md) | Follow-up B (ChatGPT): same core + seismological "why" — magnitude-type mixing, 1964 Alaska duplicate (`8.5` + `8.4`), `178` vs `100` count gap since 1900, live 2025 Kamchatka failure (`8.0 Mi` vs `8.8 Mww`) |
| [`blogpost-independent-verification-muse-spark-1.2.md`](https://github.com/straycatcoder/mathematica_learning/tree/main/blogs/earthquakedata/blogpost-independent-verification-muse-spark-1.2.md) | Independent live verification (muse-spark-1.2, Sept 4, 2026): local `wolframscript` + USGS FDSN checks; head-to-head of A vs B — both correct on essentials, B is a strict superset |
| [`blogpost-independent-verification-muse-spark-1.3.md`](https://github.com/straycatcoder/mathematica_learning/tree/main/blogs/earthquakedata/blogpost-independent-verification-muse-spark-1.3.md) | Re-run of the verification under muse-spark-1.3: fresh `wolframscript` + USGS `curl` log; reproduces the 1.2 pass exactly |
| [`blogpost.webarchive`](https://github.com/straycatcoder/mathematica_learning/tree/main/blogs/earthquakedata/blogpost.webarchive) | Archived copy of Ammon's original 2017 post |
