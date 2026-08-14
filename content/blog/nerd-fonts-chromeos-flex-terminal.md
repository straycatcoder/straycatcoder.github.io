+++
title = "Enable Nerd Fonts in the ChromeOS Flex Terminal"
date = "2026-08-14T09:30:00-04:00"
draft = false
description = "How to enable Nerd Font in the ChromeOS Flex Terminal."
tags = ["ChromeOS-Flex", "Tips"]
+++
In ChromeOS Flex, the Terminal is the entry point to Linux. In terminal settings, there are plenty of built-in fonts, however, there isn't a simple way to install nerd font or any other font, and the terminal can't pick up the fonts installed in the Linux either. 

Here is a walkaround to install a nerd font for the Terminal. 

## Nerd fonts
First, go to [Nerd Fonts](https://github.com/ryanoasis/nerd-fonts) and find the font.
Then copy the url to the font file (*.tff).

## Load a nerd font in Terminal
Open the teminal, press Ctrl+Shift+J inside Terminal and paste:

![Setup the nerd font in terminal](/images/blog/setup-nerd-font-terminal.png "Set up the nerd font in Terminal")

```
term_.prefs_.set('font-family', '"VictorMono Nerd Font", monospace');

term_.prefs_.set('user-css-text', '@font-face { font-family: "VictorMono Nerd Font"; src: url("https://raw.githubusercontent.com/ryanoasis/nerd-fonts/refs/heads/master/patched-fonts/VictorMono/VictorMonoNerdFont-Regular.ttf") format("truetype"); font-weight: normal; font-style: normal; } @font-face { font-family: "VictorMono Nerd Font"; src: url("https://raw.githubusercontent.com/ryanoasis/nerd-fonts/refs/heads/master/patched-fonts/VictorMono/VictorMonoNerdFont-Bold.ttf") format("truetype"); font-weight: bold; font-style: normal; } x-row { text-rendering: optimizeLegibility; font-variant-ligatures: normal; font-style: italic; }')
```
The terminal font shall be immediatelly updated, a simple test shows the nerd font installed correctly.

![Test the nerd font in terminal](/images/blog/test-nerd-font-terminal.png "Test the nerd font in Terminal")
