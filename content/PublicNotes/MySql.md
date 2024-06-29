---
title: MySql
Date created: 2024-06-20 14:52
Aliases:
tags: 
  - Public
---

To access MySql on a Windows machine use MySql Command Line 

> [!Info]
To Access MySql on Windows the MySql service must be running. 
Go to `Control Panel -> Windows Tools -> Services -> mysql80` or equivalent and start the service
### Starting a Server
Run the `myslqd` from it's location. For example:
```cmd
C:\> "C:\Program Files\MySQL\MySQL Server 8.4\bin\mysqld"
```

## Creating a Database

```
CREATE DATABASE <database_name>;
GRANT ALL ON <database_name>.* TO '<username>'@'localhost';
USE <database_name>
```