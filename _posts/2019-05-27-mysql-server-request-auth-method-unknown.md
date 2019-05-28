---
layout: default
title:  "MySQL 8.0 error:  The server requested authentication method unknown to the client"
---

A few days ago, after trying to create a Migration using MySQL 8.0, I've been through this error:

```
In AbstractMySQLDriver.php line 106:

  An exception occurred in driver: SQLSTATE[HY000] [2054] The server requested authentication method unknown to the client


In PDOConnection.php line 31:

  SQLSTATE[HY000] [2054] The server requested authentication method unknown to the client


In PDOConnection.php line 27:

  SQLSTATE[HY000] [2054] The server requested authentication method unknown to the client


In PDOConnection.php line 27:

  PDO::__construct(): The server requested authentication method unknown to the client [caching_sha2_password]

```

Accoring to this post on [Stack Overflow](https://stackoverflow.com/questions/52364415/the-server-requested-authentication-method-unknown-to-the-client-php):

**By default and for some reason, mysql 8 default plugin is auth_socket.**


Then, to solve this error, you can just change the password encryption algorithm to the default one, *mysql_native_password*, as follows:


1 - Connect into your mysql instance/container;

2 - Run the following command: `ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password
BY 'password';`

3 - Then try to run the migration again.

4 - Alternatively, you can edit your `my.cnf` file and force the `default_authentication_plugin` to `mysql_native_password` value, so all new users created from now on will have their passwords on the default password algorithm.

```
[mysqld]
default_authentication_plugin= mysql_native_password
```



**Important: This happens because the PHP mysqli connector is not yet compatible with new versions of MySQL. So keep in mind that this is a temporary workaround and must be fixed before deploying into production.**

[You can also find the complete description of this problem here](https://mysqlserverteam.com/upgrading-to-mysql-8-0-default-authentication-plugin-considerations/).

