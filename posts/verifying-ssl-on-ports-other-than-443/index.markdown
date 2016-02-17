---
layout: post
title:  Verifying SSL on custom ports
date:   2011-08-29 00:00:00 +0000
category: Posts
---

Your shiny new SSL needs to operate on specific ports. How do you check you've installed correctly?

If you want to verify SSL is installed correctly on other ports, you need to dig deeper.

```
openssl s_client -connect my.domain.com:465
openssl s_client -connect my.domain.com:993
```

This example shows incoming and outgoing mail connections.