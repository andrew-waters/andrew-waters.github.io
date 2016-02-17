---
layout: post
title:  NGINX with Upload Progress
date:   2012-12-31 00:00:00 +0000
category: Posts
---

Using NGINX as a load balancer can be great. Monitoring upload progress to feed back to your user doesn't come out the box.

If you need to install NGINX with upload and upload_progress modules (more than likely if you're using an FES) you can either compile by source with the additional modules installed or instead install the extras version on Ubuntu:

```
sudo apt-get install nginx-extras
```