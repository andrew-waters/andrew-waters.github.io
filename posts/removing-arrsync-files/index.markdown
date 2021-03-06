---
layout: post
title:  Removing arRsync Files
date:   2010-02-16 00:00:00 +0000
category: Posts
---

You like to backup. It make syou feel warm inside when your head hits the pillow. Until you find crap littered in your dirs.

For a while I'd been using the handy little [arRsync](http://arrsync.sourceforge.net/) to backup both the office XServe and my personal desktop machine at the office. However, I've recently introduced a new backup system and moved away from arRsync for it. The problem is, it leaves loads of sync files around the client and server machines.

All the files that syncing leaves behind to reference next time use a prefix (".._FILENAME.EXT.RAND") that means that the OS X filesystem still displays these (they're not hidden "." files!) and then displays them at the top of the finder browser (really annoying when navigating multiple directories).

So with a new backup process in place it was time to banish the files, but it has to be automated task (because of the fact there are so many files in each directory - it would take a day!).

So, terminal to the rescue - in case you find yourself with thousands of these files, this quick command may come in handy:

```
find /Volumes/MOUNT/ -name ".._*" -exec mv '{}' /Volumes/System/Users/USERNAME/Desktop/rsyncFiles \;
```

This places them all on your desktop in one folder. I did this so I could have a look at just how many files were generated by the backups process.

In my desktops case it was 42,209 files weighing in at 427.9MB. I wasn't expecting that!