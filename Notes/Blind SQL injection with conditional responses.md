---
Title: Blind SQL injection with conditional responses
tags:
  - Labs
  - BLINDSQL
  - SQLi
---
1. Intercept a request on the category functionality
![[Pasted image 20250515180737.png]]
The query may be as follows:
`SELECT TrackingId FROM TrackedUsers WHERE TrackingId = 'aLACVVqYwLHJqH42'`
2. Check for sqli
> This does not return welcome
![[Pasted image 20250515180947.png]]
![[Pasted image 20250515181015.png]]
> This one returns Welcome
![[Pasted image 20250515181057.png]]
![[Pasted image 20250515181138.png]]
3.  Slowly build the administrator's password
![[Pasted image 20250515181633.png]]
