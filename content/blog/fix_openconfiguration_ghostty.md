+++
title = 'Fix Open Configuration in Ghostty'
date = '2026-09-16T13:38:10-04:00'
draft = true
description = "Fix Ghostty "open configuration" issue in ChromeOS"
tags = ["ChromeOS-Flex", "Ghostty","Tips"]
+++

Ghostty has a shortcut "Ctrl+," to open the configuration file, under ChromeOS Flex, this short does nothing. 

To find out which application opens the configuration file, run the following command: 
```
xdg-open ~/.config/ghostty/config
```
It opens the file with Emacs in terminal mode on my machine, and setting it to open with the normal Emacs solves the issue.
```
xdg-mime default emacs.desktop text/plain
```
Linux under ChromeOS runs inside a container sandbox, it has many quirks that are unique to this environment, so far nothing has been a deal-breaker yet. 

