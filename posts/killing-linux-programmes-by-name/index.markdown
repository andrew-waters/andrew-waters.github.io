---
layout: post
title:  Killing Linux programmes by name
date:   2011-08-29 00:00:00 +0000
category: Posts
---

You're forking about with PHP - way to go! Then it spawns itself because of a bad dev script and you need to kill it in a jiffy.

Sometimes you need to be able to quickly kill a number of processes on the server that all share the same name.

```
killcli () { 
	kill -9 `ps ax | grep cli.php | grep -v grep | awk '{print $1}'`
}
```

Place the function inside your ~/bashrc file and then call the function name from the commandline. In this example we'd call:

`# killcli`