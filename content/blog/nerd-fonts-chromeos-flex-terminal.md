+++
title = "Enable Nerd Fonts in the ChromeOS Flex Terminal"
date = "2026-08-14T09:30:00-04:00"
draft = false
description = "Load a Nerd Font in the ChromeOS Flex Terminal with a user-CSS workaround — plus the easier Tilix alternative."
tags = ["ChromeOS-Flex", "Linux", "Terminal", "Tips"]
+++
In ChromeOS Flex, the Terminal is the entry point to Linux. Terminal settings include plenty of built-in fonts.

However, there is no simple way to install a Nerd Font or any custom font, and the Terminal cannot pick up fonts installed inside Linux either.

<!--more-->

Here is a workaround to load a Nerd Font in the Terminal.

## Nerd Fonts

First, go to [Nerd Fonts](https://github.com/ryanoasis/nerd-fonts) and find the font you like.

Then copy the URL of the font file (*.ttf).

## Load a nerd font in Terminal
Open the Terminal, press Ctrl+Shift+J inside Terminal and paste:

![Terminal preferences showing where to paste the Nerd Font CSS](/images/blog/setup-nerd-font-terminal.png "Set up the Nerd Font in Terminal")

```
term_.prefs_.set('font-family', '"VictorMono Nerd Font", monospace');

term_.prefs_.set('user-css-text', '@font-face { font-family: "VictorMono Nerd Font"; src: url("https://raw.githubusercontent.com/ryanoasis/nerd-fonts/refs/heads/master/patched-fonts/VictorMono/VictorMonoNerdFont-Regular.ttf") format("truetype"); font-weight: normal; font-style: normal; } @font-face { font-family: "VictorMono Nerd Font"; src: url("https://raw.githubusercontent.com/ryanoasis/nerd-fonts/refs/heads/master/patched-fonts/VictorMono/VictorMonoNerdFont-Bold.ttf") format("truetype"); font-weight: bold; font-style: normal; } x-row { text-rendering: optimizeLegibility; font-variant-ligatures: normal; font-style: italic; }')
```
The terminal font updates immediately. A quick test confirms the Nerd Font is installed correctly.

![Terminal output proving the Nerd Font glyphs render correctly](/images/blog/test-nerd-font-terminal.png "Test the Nerd Font in Terminal")

## Another way

Just install a terminal app and use the Nerd Font inside Linux — this is probably the easiest way.
The screenshot below shows the Tilix terminal with JetBrainsMono Nerd Font.

![Tilix terminal using the JetBrainsMono Nerd Font](/images/blog/nerd-font-tilix-terminal.png "Nerd Font in Tilix Terminal")

