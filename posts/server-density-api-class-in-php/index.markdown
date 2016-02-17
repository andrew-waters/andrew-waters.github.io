---
layout: post
title:  Server Density API Class in PHP
date:   2011-11-29 00:00:00 +0000
category: Posts
---

You love to write tools for your systems, your external is Server Density and you write in PHP. Oh Hai.

There are a whole host of tools available to monitor your infrastructure and application performance in the datacentre / cloud and one that I use daily is [Server Density](http://www.serverdensity.com/). They recently announced an API to access the stats (via [Mashery](http://mashery.com/)) and so it was time to build in some extra tools into the band-x Media platforms.

## Servers != Devices

Boxed Ice [recently announced](http://blog.boxedice.com/2011/08/30/announcing-agentless-monitoring-with-api-1-3/) the movement away from "servers" and into "devices". The idea here, or the way I've interpreted it, is that you can set up a device that's not necessarily associated with a piece of hardware, or a VM. The SD agent still runs on an OS and posts back to the device, but we can now monitor arbitrary stats across an entire system, not just hacking back to one device via the device API.

I'd previously written a Python plugin for the agent  which collected system information, but this was not ideal because the stats had to be placed next to a web node, and the web node has to process the stats to send back the value. Now we can simply write some scripts on any machine and when we have some stats, postback via the API to the 'device'.

The application is made up of several VM's not shown here - there are web nodes, database servers and "service" machines that take load away from the web nodes by handling third party service requests and API calls.

So now, any node can postback stats to "Freedom App" - which can have separate alerts set up - so if NR_Reponse_Time gets too high, that's an indication that the site is loading slowly). Instead of monitoring several servers to see this, that single metric is stable, application wide and easy to monitor. If an alert fires, you can then check the stats of the other machines.

## The API Class

So, in order to postback these stats, you need to interface with the SD API. Since Freedom is mainly written in PHP, I decided to write a new class for it and release under the [GPL](http://opensource.org/licenses/gpl-3.0.html) it for anyone to use. [Go get it from Github](https://github.com/andrew-waters/Server-Density-API).

Of course, you don't have to use it to postback device stats. You can get the full suite of API methods provided so you can build in your own business logic to the monitoring suite.

Using it is simple. Simply add your credentials to file, include it in your app, instantiate and then make your calls, such as:

```
$api = new ServerDensityAPI;
$api->setCall("devices", "list")->call();
if($api->response->status == 1) {
    // the call has been successful
    print_r($api->response->data);
}
```

[This code](http://pastebin.com/Zd49tz0M) will get all of your devices and pull out the load and memory consumption for each device.

## Conclusion

The incrementation of the API is a very welcome one from my side. From a sysadmin point of view, you can never have too much control of your systems and the more tools you have at your disposal, the better prepared you are to deal with the inevitable situations you need to deal with.

I hope [the class](https://github.com/andrew-waters/Server-Density-API) gets you up and running that bit quicker.