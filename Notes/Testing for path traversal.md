---
Title: Testing for path traversal
tags:
  - path-traversal
---
# What is path traversal?
This is a type of bug / vulnerability in an application, where an attacker is able to access or read arbitrary files on the server that is running on an application.

> [!Example]
> ```bash 
> https://insecure-website.com/loadImage?filename=../../../../etc/passwd
> # this is fundamentally it.
> https://insecure-website.com/loadImage?filename=..\..\..\windows\win.ini # for windows

If your simple case payload [[File path traversal, simple case|../../../etc/passwd]] does not work, we can try and use absolute paths instead of the traditional one [[File path traversal, traversal sequences blocked with absolute path bypass | /etc/passwd]].

Another case is if the application escapes the text `../`, but this is rather ineffective if the application only escapes / removes that sequence only once. We can bypass it by using [[File path traversal, traversal sequences stripped non-recursively|....//....//....//....//etc/passwd]]

If the application does an initial url-decode of the payload, we could use a double url-encoded payload, like in this example here [[File path traversal, traversal sequences stripped with superfluous URL-decode]].

For example, the application requires a 


