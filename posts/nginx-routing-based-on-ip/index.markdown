---
layout: post
title:  NGINX Routing based on IP
date:   2014-04-18 00:00:00 +0000
category: Posts
---

Sometimes you want to connect to a different set of upstream nodes from an NGINX load balancer.

When you're creating load balancing configurations in NGINX, sometimes you are going to want to route traffic from a certain IP address to a different set of upstream nodes. This may be because you have a CI environment which uses the same load balancer (staging) or could be for other reasons.

Regardless, create your alternative upstream:

```
upstream defaultNodes {
	server 192.168.1.1;	# default nodes...
}

upstream alternativeNodes {
	server 192.168.1.100;	# new nodes...
}
```

Then in the server directive, add the condition (assuming the public IP you want to route is 100.0.0.1):

```
location / {

	proxy_pass http://defaultNodes/;

	if ( $remote_addr ~* 100.0.0.1 ) {
		proxy_pass http://alternativeNodes;
	}

}
```