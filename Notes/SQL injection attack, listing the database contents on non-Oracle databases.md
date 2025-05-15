---
Title: SQL injection attack, listing the database contents on non-Oracle databases
tags:
  - Labs
  - SQLi
---
1. Intercept a request on the filter category feature
![[Pasted image 20250515153853.png]]
2. Test for SQLi and see what works
![[Pasted image 20250515154025.png]]
3. Test for UNION attacks
![[Pasted image 20250515154100.png]]
4. Query the table_name
![[Pasted image 20250515155057.png]]
5. Query the column name of the table we found
![[Pasted image 20250515155214.png]]
6. Query the contents of the table `users_eyzsbs`
![[Pasted image 20250515160443.png]]
7. Login as administrator



