---
layout: post
title:  Mitigating NTP attacks against ESXi 4.1
date:   2014-05-01 00:00:00 +0000
category: Posts
---

The `monlist` command against NTP servers is being used to launch DDOS attacks.

ESXi 4.1 contains a vulnerability that can be used to create an amplification attack using the molist command in NTP.

If you're using that version, you can mitigate the issue by editing `/etc/ntp.conf` and adding `noquery` and `nopeer` to the restrict line 

```restrict default kod nomodify notrap noquery nopeer
restrict 127.0.0.1
driftfile /etc/ntp.drift
```

Once done, restart NTP with `/etc/init.d/ntpd restart`