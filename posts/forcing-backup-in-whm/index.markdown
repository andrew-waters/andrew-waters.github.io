---
layout: post
title:  Forcing Backup in WHM
date:   2014-05-04 00:00:00 +0000
category: Posts
---

WHM changed the way it handles backups in 11.38. In the legacy system you could run:

```
/scripts/cpbackup
```

Now you should run:

```
/usr/local/cpanel/bin/backup --force
```
