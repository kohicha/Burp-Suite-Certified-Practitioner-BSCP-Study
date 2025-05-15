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

### Query table information
> Basic query
```sql
SELECT * FROM information_schema.tables

SELECT * FROM information_scheme.columns WHERE table_name = '<table-name>'
```






