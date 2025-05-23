---
Title: CSRF where token is not tied to user session
tags:
  - Labs
  - CSRF
---
# Testing our payload
1. Login on both accounts, use firefox and burp browser.
2. Generate a csrf poc from carlos account
![[Pasted image 20250523160106.png]]
3. post the payload to exploit server with the creds of wiener logged in
![[Pasted image 20250523160243.png]]
4. we can see that the payload has successfully changed wiener's password
![[Pasted image 20250523160322.png]]

# Final payload
1. Intercept another request and generate csrf payload
![[Pasted image 20250523160508.png]]
2. send to exploit server, send to victim, and we get, MONEY!
![[Pasted image 20250523160544.png]]







