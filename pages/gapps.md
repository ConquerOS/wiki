---
sidebar: home_sidebar
title: Google apps
permalink: gapps.html
---
Google apps are the proprietary Google-branded applications that come pre-installed with most Android devices, such as the Play Store, Gmail, Maps, etc.
Due to licensing restrictions, these apps cannot come pre-installed with ConquerOS and must be installed separately. The Google apps are not required to
boot or run ConquerOS, however many users find them beneficial to take full advantage of the Android ecosystem.

These apps have been packaged by developers independent of ConquerOS, and download links have been provided for your convenience only. It is possible to perform
a "backup" of the Google apps on your device and then "restore" them, but this does take additional steps which are not covered here.

The Google apps packages are **not included** in any way by ConquerOS.

## Downloads

These packages are only dependent on your OS version and architecture, which can be found on each device specific info page in this wiki ([Device overview](devices.html)).

{% include alerts/note.html content="If you opt to use Open GApps, they offer a variety of sizes of packages that include and overwrite different apps. We only recommend package sizes up through `nano`, as described in [Open GApps Package Comparison](https://github.com/opengapps/opengapps/wiki/Package-Comparison). If you use a larger package, we can not guarantee that everything will function on your device, as in many of these cases our included apps are overwritten in favor of the Google App equivalents." %}

## Installation

Google apps should be installed via recovery **immediately** after installing ConquerOS. Exact steps vary, and as such, you should see your device's installation guide [here](https://wiki.conqueros.co/devices/) for specific instructions.

{% include alerts/important.html content="If you reboot into ConquerOS before installing Google apps, you must factory reset and then install them, otherwise expect crashes." %}
