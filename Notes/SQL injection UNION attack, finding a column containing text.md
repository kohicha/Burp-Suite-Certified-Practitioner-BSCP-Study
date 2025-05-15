---
Title: SQL injection UNION attack, finding a column containing text
tags:
  - Labs
  - SQLi
  - UNIONATTACKS
---
# SQL injection UNION attack, finding a column containing text
1. Grab a request in Burp
![[{0D2EB239-82B2-4633-912D-405083EE6426}.png]]
2. Use the payload we used in [[SQL injection UNION attack, finding a column containing text]]
3. Test out each "NULL" column, and insert the text required to solve the lab
![[{AED50325-2AB5-47E7-B18F-23B718BF2979}.png]]






