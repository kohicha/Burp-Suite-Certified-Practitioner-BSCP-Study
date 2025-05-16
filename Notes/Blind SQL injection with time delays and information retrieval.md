---
Title: Blind SQL injection with time delays and information retrieval
tags:
  - Labs
  - BLINDSQL
  - SQLi
---
1. Intercept a request from the filter category functionality
![[Pasted image 20250517001622.png]]
2. Test for time-based sqli in the trackingId
![[Pasted image 20250517001849.png]]
3. Create a payload to extract the administrator password, via substring matching
![[Pasted image 20250516194624.png]]
4. Continue the payload in intruder and extract the password
![[Pasted image 20250516194643.png]]






