---
title: "XSS-01"
date: 2022-08-08T02:51:30-04:00
draft: false
description: It seems harmless, does it?
categories: OWASP Top10
featured_image: "images/xss01.jpg"
images: ["images/xss01.jpg"]

tags: [XSS]
---

# XSS

## Types

- Reflected XSS

  Typically, to exploit a reflected xss, you need to send the vulnerable link to victim that contains xss payload, which could send you information of the victim such as cookies. In addition, it's better to know to obfuscate the URL

- Persistent/Stored XSS

  In contrast to Reflected XSS, the payload is stored in server side which mean the victim will be affected by XSS everytime he entered the vulnerable web application

- DOM XSS

  To simplify, it exists **only within client-side code** (javascript). It's similar to Reflected XSS but without interacting with server-side. 

  In Reflected XSS, the payload are already in the response from the web server, then it's showed or exploited on the client side. 

  In DOM XSS, the response from the web server have no malicious payload, to the server's perspective, everything looks the same, except on client side, **the browser** take the parameter from the url, then execute the payload.

  ```javascript
  # source: where the untrusted input is handled
  var search = document.getElementById('search').value;
  var results = document.getElementById('results');
  # sink: where the untrusted input is used
  results.innerHTML = 'You searched for: ' + search;
  ```

