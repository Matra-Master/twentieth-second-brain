---
created: 20230217-0957
tags:
  - mysql
---

## CLI

``` bash
mysql -u user -p
```

Access a database to work on

``` mysql
    USE database_name;
    SHOW TABLES;
```

You can show tables from a DB without switching to it

``` mysql
    SHOW TABLES FROM database_name;
```

Concatenate multiple repeated queries into a list for every table

``` mysql
SELECT CONCAT("ALTER TABLE ", TABLE_SCHEMA, '.', TABLE_NAME," COLLATE your_collation_name_here;") 
AS ExecuteTheString
FROM INFORMATION_SCHEMA.TABLES
WHERE TABLE_SCHEMA="YourDatabaseName"
AND TABLE_TYPE="BASE TABLE";
```

dump something prompting for password

``` bash
mysqldump -u [user] -p [table] > [filename].sql
```

Restore from a dump file

``` bash
mysql -u [user] -p [table] < [filename].sql
```

update something

```mysql
UPDATE tablename  
SET column1 = value1, column2 = value2,
WHERE condition;
```

Get password policy
```mysql
SHOW VARIABLES LIKE 'validate_password%';
```

## Users

List all users for mysql
``` mysql
SELECT * FROM mysql.user;
SELECT User,Host FROM mysql.user;
```

Show a user's permissions
```mysql
SHOW GRANTS FOR '<user>'@'<host>';
```

## Deletions

``` mysql
DROP DATABASE <DB_NAME>;
```

``` mysql
DROP USER <USER_NAME>@<HOST_NAME>;
```
