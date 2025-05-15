---
Title: Testing for SQLi
tags:
  - SQLi
---
# Testing for SQLi
To test whether sqli is possible, we have to manually do these "checks", if an sqli is possible to exploit. 

Boolean based sqli

`'OR 1 = 1--`

# Querying the database
| DATABASE         | QUERY                     |
| ---------------- | ------------------------- |
| Microsoft, MySQL | `SELECT @@version`        |
| Oracle           | `SELECT * FROM v$version` |
| PostgreSQL       | `SELECT version()`        |








