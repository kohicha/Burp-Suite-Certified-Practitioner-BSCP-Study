---
Title: CSRF where token validation depends on request method
tags:
  - Labs
  - CSRF
---
1. Log in as wiener, and intercept a change email post request
![[Pasted image 20250523153201.png]]
2. Generate a CSRF Payload.
![[Pasted image 20250523153426.png]]
Copy the payload and paste it in the exploit server, store it and deliver exploit to victim.
![[Pasted image 20250523153905.png]]

> [!warning] Note
> The generated csrf poc has a method on the post form. Remove that to generate a GET request on the poc.










