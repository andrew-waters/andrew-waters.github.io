---
layout: post
title:  Hard reboot of Server
date:   2011-11-02 00:00:00 +0000
category: Posts
---

You never want to do it, you should never need to, but sweet mary when you have to, beware of hangs.

Sometimes when you run a "sudo reboot now" a couple of processes can get stuck and cause the system to hang. It's usually worth creating a new SSH connection before you start the boot and connect to the server. If the first reboot fails, run this in the second connection:

```
echo 1 > /proc/sys/kernel/sysrq
echo b > /proc/sysrq-trigger
```

This will tell the system to perform an immediate reboot without running through the normal shutdown sequeneces.