---
layout: post
title:  Sharing Profiles via Dropbox
date:   2012-07-06 00:00:00 +0000
category: Posts
---

Great for sharing files. Great for sharing bash profiles. Great for sharing SSH keys. Great for the NSA.

```
ln -s ~/Dropbox/.shared/.ssh ~/.ssh
ln -s ~/Dropbox/.shared/.bash_profile ~/.bash_profile
```

You may run into problems with permissions, so be sure to run the following:

```
chmod 700 ~/.ssh
chmod 600 ~/.ssh/id_rsa
chmod 644 ~/.ssh/id_rsa.pub  
chmod 644 ~/.ssh/authorized_keys
chmod 644 ~/.ssh/known_hosts
```

Now you can use the same key on all machines. Boom goes the dyn-o-mite.