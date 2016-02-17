---
layout: post
title:  Casting fields in MongoDB Docs
date:   2013-07-16 00:00:00 +0000
category: Posts
---

So you have your document schema sorted but your application is throwing in mixed types on an indexed field.

Not the end of the world, but your indexes are performing sub optimally. Hit up your MongoShell:

```
db.runCommand({
	$eval : db.COLLECTION_NAME.find({
		FIELD_NAME : {
			$exists : true,
			$type : 2
		}
	}).forEach( function(obj) {
		obj.FIELD_NAME = new NumberInt(obj.FIELD_NAME);
		db.COLLECTION_NAME.save(obj);
	}),
	nolock: true
})
```

All types have a numeric identifier and a [full list can be seen here](http://www.mongodb.org/display/DOCS/Advanced+Queries#AdvancedQueries-%24type).

Much quicker than processing type operators on the application side. However, large collections will lock the database so your mileage will vary!
