---
Title: Visible error-based SQL injection
tags:
  - Labs
  - ERROR-BASEDSQLi
  - SQLi
---
1. Intercept a request
![[Pasted image 20250515222410.png]]
2. Test the CAST() method
![[Pasted image 20250515222509.png]]
3. Try to get some information
![[Pasted image 20250515222600.png]]
![[Pasted image 20250515222608.png]]
There seems to be a character limit, let's remove the token.
![[Pasted image 20250515222637.png]]
![[Pasted image 20250515222652.png]]
4. Create a working payload, and login as admin.
![[Pasted image 20250515222727.png]]
![[Pasted image 20250515222742.png]]



