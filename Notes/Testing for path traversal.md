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
 


