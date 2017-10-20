## Put the following in the file challenges/labs/1_mysql.md

### The hostname of your MySQL node

```bash
$ hostname
ip-172-31-25-233.eu-central-1.compute.internal
```

### The command and output for mysql --version
```bash
# mysql --version
mysql  Ver 14.14 Distrib 5.5.58, for Linux (x86_64) using readline 5.1
```

### The command and output for listing MySQL databases

```sql
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| hue                |
| metastore          |
| mysql              |
| oozie              |
| performance_schema |
| rman               |
| scm                |
| sentry             |
+--------------------+
9 rows in set (0.00 sec)
```