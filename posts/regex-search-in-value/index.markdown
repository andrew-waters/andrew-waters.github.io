---
layout: post
title:  Regex Search in value
date:   2011-09-26 00:00:00 +0000
category: Posts
---

I'll never be able to class myself as an engineer - I don't use regex nearly enough. But it has it's time and place in my cycle.

Use MongoDB to find a regex term inside it's content (PHP flavoured)

```
MyClass::find(array(
	'thanks.for' => array(
		'$regex' => "/*understanding*"
	)
));
```