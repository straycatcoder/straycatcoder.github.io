+++
title = 'Reset the Browser in Linux Container'
date = '2026-09-15T13:10:48-04:00'
draft = false
description = "Reset the default browser in the Linux container to the Chrome browser."
tags = ["Tips","ChromeOS-Flex","Terminal", "Linux"]
+++

I installed ChatGPT desktop inside Linux container on ChromeOS Flex, one issue is that it hijacks the browser setting: clicking a web link in the Linux terminal, it launches the ChatGPT desktop and does nothing with the URL.

ChromeOS handles cross-system actions using a background service called Garcon. To force your terminal to always route links to the ChromeOS Chrome browser, you just need to set Garcon as your default web browser inside the container.

```
unset BROWSER # it may not be necessary, troubleshooting only
xdg-settings set default-web-browser garcon_host_browser.desktop
```

Now, whenever Ctrl-clicking a URL in the terminal, it will open instantly in a new tab on the Chrome browser.

