---
layout: post
title:  Mongo PHP Extension in MAMP
date:   2011-08-18 00:00:00 +0000
category: Posts
---

Some things really shouldn't need notes. Adding the PHP MongoDB extension on MAMP does.

I decided to move my web interface to my [MongoDB](http://www.mongodb.org/) servers to my local machines so they weren't exposed on the internet. Whilst I built some simple IP verification to [Rock Mongo](http://code.google.com/p/rock-php/), when my IP starts floating, it means editing a config file, which is easy but a bit of a pain.

So to solve this, I run a local copy on my desktop, which also has a copy of [MAMP Pro](http://www.mamp.info/en/mamp-pro/) on. Since Rock Mongo is written in PHP, it kinda makes sense to use it.

If you want to run Mongo locally, just run through their installation process. In my case, I'm connecting to remote servers, so I don't need it for this demonstration.

It turns out that getting the Mongo driver for PHP in MAMP is pretty straightforward, but there's a gotcha.

First up, head over and download the [OS X binary](https://github.com/mongodb/mongo-php-driver/downloads) for the version of PHP you're running (in my case 5.3).

Once downloaded, extract the archive and put the mongo.so binary inside MAMP's PHP extensions directory:

```
/Applications/MAMP/bin/php5.3/lib/php/extensions/no-debug-non-zts-XXXXXXXX
```

Next comes the gotcha. We need to tell PHP that we want the extension loaded, which is done in your php.ini file (this is PHP's configuration file).

But, if you edit the file directly, it will be overwritten the next time the server is loaded. This is because MAMP has a template php.ini file which is loaded into place each time Apache is started up. So, to edit the template file, switch into MAMP and go to 'File > Edit Template > PHP 5.X.X php.ini'

This will load up the editor for the config file. Simply go to ~line 530 where your dynamic extensions are listed and add the following to a new line:

```
extension=mongo.so
```

Restart Apache via MAMP and you should have yourself a nice, easy MongoDB driver ready to play with.