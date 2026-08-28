+++
title = 'Test Local Wolfram MCP'
date = '2026-08-28T10:09:45-04:00'
draft = false
description = ""
tags = ["AI","Wolfram", "ChatGPT", "Animation"]
+++
In the past, I occasionally tried to use AI to test some novel visualization ideas with Wolfram, it doesn't matter which AI (Claude, ChatGPT or Gemini) used, most of time, the generated code is barely usable at most.

Now with Wolfram MCP, the AI model shall be able to produce much better code. I saw [507 Mechanical Movements](https://507movements.com/) from Hackernews. Let's have some fun with it.

Two simple cases from the front page are chosen.
| [mm_001](https://507movements.com/mm_001.html) | [mm_005](https://507movements.com/mm_005.html) | mm_style |
|---|---|---|
| <img src="/images/blog/mechanical/mm_001.png" alt="mm_001" style="height: 240px; width: auto; object-fit: contain; border-radius: 8px; display: block; margin: 0 auto;" /> | <img src="/images/blog/mechanical/mm_005.png" alt="mm_005" style="height: 240px; width: auto; object-fit: contain; border-radius: 8px; display: block; margin: 0 auto;" /> | <img src="/images/blog/mechanical/mm_style.png" alt="mm_style" style="height: 240px; width: auto; object-fit: contain; border-radius: 8px; display: block; margin: 0 auto;" /> |

**Inputs**: the static black/white image and the description on the movement from the website. The third color image is used as the style guide.

**AI**: ChatGPT with GPT 5.6 Terra (medium)

Animated results after an half hour session.

| mm_001 animation | mm_005 animation |
|---|---|
| <img src="/images/blog/mechanical/mm_001ani.gif" alt="mm_001 animation" style="height: 400px; width: auto; object-fit: contain; border-radius: 8px; display: block; margin: 0 auto;" /> | <img src="/images/blog/mechanical/mm_005ani.gif" alt="mm_005 animation" style="height: 400px; width: auto; object-fit: contain; border-radius: 8px; display: block; margin: 0 auto;" /> |

**mm_001**: AI pretty much gets it done in first shot, only missing some details of the inner spikes in pulleys.  
**mm_005**: this one is tough, it is not problem from AI, the description from the website is more complex than the animation. It needs several extra instructions to get the animation done.

> Resembles 1, with the addition of a movable tightening pulley, B. When this pulley is pressed against the band to take up the slack, the belt transmits motion from one of the larger pulleys to the other; but when it is not, the belt is so slack as not to transmit motion.

So the following animation generated from AI is probably more close to the original description. The belt is wrapped too much around part B in the end, Once you points out this issue, AI will fix it by calculating the tangents to make the rope only touch the part B at the rightmost edge.

<img src="/images/blog/mechanical/mm_005_ani_01.gif" alt="mm_005_ani_01" style="height: 400px; width: auto; object-fit: contain; border-radius: 8px; display: block; margin: 20px auto;" />

**Conclusions**: Yes, Wolfram MCP is great, and improves AI coding quality. 

