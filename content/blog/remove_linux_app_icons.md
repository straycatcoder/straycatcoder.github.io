+++
title = 'Remove Linux App Icons'
date = '2026-11-04T09:38:18-05:00'
draft = false
description = "How to Remove Leftover Linux App Icons"
tags = ["ChromeOS-Flex","Linux","Tips"]
+++
Sometimes after removing an app from ChromeOS Linux, its icon may still appear in ChromeOS Launcher.
![Linux app in ChromeOS Launcher](/images/blog/Linux_app_icons.png "Linux app in ChromeOS Launcher")

In debian, the icons are defined by desktop entries (*.desktop). 
Check the following two places to remove the leftover desktop entries.

```bash
# User-Specific Applications
~/.local/share/applications/

# System-Wide Applications
/usr/share/applications/
```
Once the desktop file is deleted, the lingering icon will disappear from ChromeOS Launcher.

Similarly, you can also create a .desktop file to make an app accessible from the launcher.
