title: Liberating my Server from (MariaDB) Database Logs
date: 2025-12-03 13:58 -0700
tags: MariaDB, Home Assistant, Docker


My server running Docker seems forever to be low on space. So I finally got
annoyed at it enough to figure out what was going on and try and fix it.

First, I needed to figure out what was taking up soooo much space. `ncdu` --
which was even already installated! -- was the tool of choice. And it promptly
found 63.8GB (on a 256GB drive) in `docker/volumes/homeassistant-db/logs/mysql`;
all binary logs.

![ncdu]({static}images/2025/ncdu-mariadb-logs.png)

I have logs going back over a year, but I never look at them. So how best to
clean these up?

First, I looked into automatic log rotation, which should keep some of the
newer logs (allowing me to look for recent issues, if needed) but automatically
remove older ones. Looking at the config file, it seems to be set up right. The
config file is at `docker/volumes/homeassistant-db/custom.cnf` and the lines of
interest:

``` { .ini linenos=true linenostart=129 }
expire_logs_days        = 10
max_binlog_size         = 100M
```

This is saying that the log files have a (soft) size limit of 100 MB (which
seems to be being respected) and that logs older than 10 days should
automatically be deleted (which isn't being respected).

Ok, let's see if I can manually rotate the logs. To do this, I need a shell in
the MariaDB Docker container; I have *Portainer* set up to allow me to do this.
Once at the shell, I run `mariadb` to get a prompt to directly edit the
database. From there, I'll drop everything older than ~1 week:

```postgres-console
MariaDB [(none)]> PURGE BINARY LOGS BEFORE '2025-11-22';
Query OK, 0 rows affected, 1 warning (0.005 sec)
```

This looks, at first glance, like it worked. However, the files are still on
disk, and there is a notation about one warning. Okay, what's the warning?

```postgres-console
MariaDB [(none)]> SHOW WARNINGS;
+-------+------+----------------------------------------------------------------------------+
| Level | Code | Message                                                                    |
+-------+------+----------------------------------------------------------------------------+
| Note  | 1375 | 'mariadb-bin.000570' is not purged because it is the current active binlog |
+-------+------+----------------------------------------------------------------------------+
1 row in set (0.001 sec)
```

Ah, no it's not the "active binlog" (or it shouldn't be); that's our first log
file still on disk, and is over a year old! But if the database server thinks
that the case, that would explian why it's keep all the logs since.

But I can dump all the logs, since I've never referred to them anyway.

```postgres-console
MariaDB [(none)]> RESET MASTER TO 1260;
Query OK, 0 rows affected (0.058 sec)
```

The `TO 1260` is optional; it sets the number that the new log files should
start with. I set it here just a couple higher than the previous most recent
log file (1257).

Success! The log files are gone!

Next up: add a sensor to Home Assistant to monitor the size of this folder...

---

References:

- [expire_log_days](https://mariadb.com/docs/server/ha-and-performance/standard-replication/replication-and-binary-log-system-variables#expire_logs_days)
  in the MariaDB configuration documentation
- [SHOW BINARY
  LOGS](https://mariadb.com/docs/server/reference/sql-statements/administrative-sql-statements/show/show-binary-logs) on MariaDB documentation
- [PURGE BINARY
  LOGS](https://mariadb.com/docs/server/reference/sql-statements/administrative-sql-statements/purge-binary-logs)
  on MariaDB documentation
- [SHOW
  WARNINGS](https://mariadb.com/docs/server/reference/sql-statements/administrative-sql-statements/show/show-warnings)
  on MariaDB documentation
- [RESET
  MASTER](https://mariadb.com/docs/server/reference/sql-statements/administrative-sql-statements/replication-statements/reset-master)
  on MariaDB documentation
- [Error
  1375](https://mariadb.com/docs/server/reference/error-codes/mariadb-error-codes-1300-to-1399/e1375)
  in the MariaDB Error Codes Reference
