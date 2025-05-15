---
Title: Enumerating the database using SQLi
tags:
  - SQLi
---
# Gathering database information
---
### Query the database version

| DATABASE         | QUERY                     |
| ---------------- | ------------------------- |
| Microsoft, MySQL | `SELECT @@version`        |
| Oracle           | `SELECT * FROM v$version` |
| PostgreSQL       | `SELECT version()`        |

### Get some information on tables 






