---
Title: Blind SQLi
tags:
  - SQLi
---
Blind SQL is not necessarily being "blind", but rather looking at other intricacies the application returns whenever you inject a query. 

> [!Sample Query]
```sql
SELECT TrackingId FROM TrackedUsers WHERE TrackingId = 'abcdefghijklmnopqrstuvwxyz'
```


