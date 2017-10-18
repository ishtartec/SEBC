## A Quick Sentry Tutorial

### Verify user privileges:

```bash
$ klist
Ticket cache: FILE:/tmp/krb5cc_1001
Default principal: ishtartec@ISHTARTEC.COM

Valid starting       Expires              Service principal
10/18/2017 08:29:50  10/19/2017 08:29:50  krbtgt/ISHTARTEC.COM@ISHTARTEC.COM
	renew until 10/25/2017 08:29:50
$ beeline
Beeline version 1.1.0-cdh5.8.3 by Apache Hive
beeline> !connect jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-24-43.eu-central-1.compute.internal@ISHTARTEC.COM
scan complete in 3ms
Connecting to jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-24-43.eu-central-1.compute.internal@ISHTARTEC.COM
Enter username for jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-24-43.eu-central-1.compute.internal@ISHTARTEC.COM: ishtartec
Enter password for jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-24-43.eu-central-1.compute.internal@ISHTARTEC.COM: ********
Connected to: Apache Hive (version 1.1.0-cdh5.8.3)
Driver: Hive JDBC (version 1.1.0-cdh5.8.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://localhost:10000/default> show tables;
INFO  : Compiling command(queryId=hive_20171018090404_dce3cf8a-13c3-4d20-a696-cbb36f2d3f38): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20171018090404_dce3cf8a-13c3-4d20-a696-cbb36f2d3f38); Time taken: 0.064 seconds
INFO  : Executing command(queryId=hive_20171018090404_dce3cf8a-13c3-4d20-a696-cbb36f2d3f38): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171018090404_dce3cf8a-13c3-4d20-a696-cbb36f2d3f38); Time taken: 0.177 seconds
INFO  : OK
+-----------+--+
| tab_name  |
+-----------+--+
+-----------+--+
No rows selected (0.252 seconds)
```

### Create a Sentry role with full authorization
```bash
0: jdbc:hive2://localhost:10000/default> CREATE ROLE sentry_admin;
INFO  : Compiling command(queryId=hive_20171018090505_77febc08-c2d3-4c12-aa5e-f45e9613ac16): CREATE ROLE sentry_admin
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171018090505_77febc08-c2d3-4c12-aa5e-f45e9613ac16); Time taken: 0.081 seconds
INFO  : Executing command(queryId=hive_20171018090505_77febc08-c2d3-4c12-aa5e-f45e9613ac16): CREATE ROLE sentry_admin
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171018090505_77febc08-c2d3-4c12-aa5e-f45e9613ac16); Time taken: 0.72 seconds
INFO  : OK
No rows affected (0.811 seconds)
0: jdbc:hive2://localhost:10000/default> GRANT ALL ON SERVER server1 TO ROLE sentry_admin;
INFO  : Compiling command(queryId=hive_20171018090505_1d219bf7-cda8-4a12-a901-53caf10d8a97): GRANT ALL ON SERVER server1 TO ROLE sentry_admin
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171018090505_1d219bf7-cda8-4a12-a901-53caf10d8a97); Time taken: 0.087 seconds
INFO  : Executing command(queryId=hive_20171018090505_1d219bf7-cda8-4a12-a901-53caf10d8a97): GRANT ALL ON SERVER server1 TO ROLE sentry_admin
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171018090505_1d219bf7-cda8-4a12-a901-53caf10d8a97); Time taken: 0.087 seconds
INFO  : OK
No rows affected (0.182 seconds)
0: jdbc:hive2://localhost:10000/default> GRANT ROLE sentry_admin TO GROUP ishtartec;
INFO  : Compiling command(queryId=hive_20171018090606_18e4e382-5467-4703-927c-90d1c0129d4f): GRANT ROLE sentry_admin TO GROUP ishtartec
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171018090606_18e4e382-5467-4703-927c-90d1c0129d4f); Time taken: 0.062 seconds
INFO  : Executing command(queryId=hive_20171018090606_18e4e382-5467-4703-927c-90d1c0129d4f): GRANT ROLE sentry_admin TO GROUP ishtartec
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171018090606_18e4e382-5467-4703-927c-90d1c0129d4f); Time taken: 0.074 seconds
INFO  : OK
No rows affected (0.146 seconds)
0: jdbc:hive2://localhost:10000/default> SHOW TABLES;
INFO  : Compiling command(queryId=hive_20171018090606_8c7a0813-6a5e-4b44-a399-bb1e6aa6f8e6): SHOW TABLES
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20171018090606_8c7a0813-6a5e-4b44-a399-bb1e6aa6f8e6); Time taken: 0.061 seconds
INFO  : Executing command(queryId=hive_20171018090606_8c7a0813-6a5e-4b44-a399-bb1e6aa6f8e6): SHOW TABLES
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171018090606_8c7a0813-6a5e-4b44-a399-bb1e6aa6f8e6); Time taken: 0.122 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0.198 seconds)
0: jdbc:hive2://localhost:10000/default>
```

### Create additional test users

Add new users to all cluster nodes
```bash
$ sudo groupadd selector
$ sudo groupadd inserters
$ sudo useradd -u 1100 -g selector george
$ sudo useradd -u 1200 -g inserters ferdinand
$ kadmin.local
> add_principal george
> add_principal ferdinand
```

### Create test roles

Login to beeline as your admin user

```bash
$ beeline
Beeline version 1.1.0-cdh5.8.3 by Apache Hive
beeline> !connect jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-24-43.eu-central-1.compute.internal@ISHTARTEC.COM
scan complete in 3ms
Connecting to jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-24-43.eu-central-1.compute.internal@ISHTARTEC.COM
Enter username for jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-24-43.eu-central-1.compute.internal@ISHTARTEC.COM: ishtartec
Enter password for jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-24-43.eu-central-1.compute.internal@ISHTARTEC.COM:
Connected to: Apache Hive (version 1.1.0-cdh5.8.3)
Driver: Hive JDBC (version 1.1.0-cdh5.8.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://localhost:10000/default> CREATE ROLE reads;
INFO  : Compiling command(queryId=hive_20171018091717_30335a80-955a-44a3-89c3-4fc31d7857ca): CREATE ROLE reads
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171018091717_30335a80-955a-44a3-89c3-4fc31d7857ca); Time taken: 0.06 seconds
INFO  : Executing command(queryId=hive_20171018091717_30335a80-955a-44a3-89c3-4fc31d7857ca): CREATE ROLE reads
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171018091717_30335a80-955a-44a3-89c3-4fc31d7857ca); Time taken: 0.044 seconds
INFO  : OK
No rows affected (0.114 seconds)
0: jdbc:hive2://localhost:10000/default> CREATE ROLE writes;
INFO  : Compiling command(queryId=hive_20171018091717_9ccc6ad4-225c-46ef-883e-7498a0cbe968): CREATE ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171018091717_9ccc6ad4-225c-46ef-883e-7498a0cbe968); Time taken: 0.057 seconds
INFO  : Executing command(queryId=hive_20171018091717_9ccc6ad4-225c-46ef-883e-7498a0cbe968): CREATE ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171018091717_9ccc6ad4-225c-46ef-883e-7498a0cbe968); Time taken: 0.025 seconds
INFO  : OK
No rows affected (0.09 seconds)
```

### Grant read privilege for all tables to reads

```bash
0: jdbc:hive2://localhost:10000/default> GRANT SELECT ON DATABASE default TO ROLE reads;
INFO  : Compiling command(queryId=hive_20171018091717_5c7dec38-b74c-4ced-b8dc-eb215a96beb8): GRANT SELECT ON DATABASE default TO ROLE reads
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171018091717_5c7dec38-b74c-4ced-b8dc-eb215a96beb8); Time taken: 0.065 seconds
INFO  : Executing command(queryId=hive_20171018091717_5c7dec38-b74c-4ced-b8dc-eb215a96beb8): GRANT SELECT ON DATABASE default TO ROLE reads
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171018091717_5c7dec38-b74c-4ced-b8dc-eb215a96beb8); Time taken: 0.04 seconds
INFO  : OK
No rows affected (0.114 seconds)
0: jdbc:hive2://localhost:10000/default> GRANT ROLE reads TO GROUP selector;
INFO  : Compiling command(queryId=hive_20171018091717_168f4d87-4361-4bca-91a6-8d4923443ae0): GRANT ROLE reads TO GROUP selector
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171018091717_168f4d87-4361-4bca-91a6-8d4923443ae0); Time taken: 0.067 seconds
INFO  : Executing command(queryId=hive_20171018091717_168f4d87-4361-4bca-91a6-8d4923443ae0): GRANT ROLE reads TO GROUP selector
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171018091717_168f4d87-4361-4bca-91a6-8d4923443ae0); Time taken: 0.029 seconds
INFO  : OK
No rows affected (0.106 seconds)
```



### Grant read privilege for default.sample07 only to 'writes':

```bash
0: jdbc:hive2://localhost:10000/default> REVOKE ALL ON DATABASE default FROM ROLE writes;
INFO  : Compiling command(queryId=hive_20171018091717_ac9384f1-4506-415b-ba56-78936f2f4aa6): REVOKE ALL ON DATABASE default FROM ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171018091717_ac9384f1-4506-415b-ba56-78936f2f4aa6); Time taken: 0.06 seconds
INFO  : Executing command(queryId=hive_20171018091717_ac9384f1-4506-415b-ba56-78936f2f4aa6): REVOKE ALL ON DATABASE default FROM ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171018091717_ac9384f1-4506-415b-ba56-78936f2f4aa6); Time taken: 0.084 seconds
INFO  : OK
No rows affected (0.155 seconds)
0: jdbc:hive2://localhost:10000/default> GRANT SELECT ON default.sample_07 TO ROLE writes;
INFO  : Compiling command(queryId=hive_20171018091818_3a3d9a4e-999a-4fb9-9907-94c7062c5a18): GRANT SELECT ON default.sample_07 TO ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171018091818_3a3d9a4e-999a-4fb9-9907-94c7062c5a18); Time taken: 0.057 seconds
INFO  : Executing command(queryId=hive_20171018091818_3a3d9a4e-999a-4fb9-9907-94c7062c5a18): GRANT SELECT ON default.sample_07 TO ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171018091818_3a3d9a4e-999a-4fb9-9907-94c7062c5a18); Time taken: 0.041 seconds
INFO  : OK
No rows affected (0.108 seconds)
0: jdbc:hive2://localhost:10000/default> GRANT ROLE writes TO GROUP inserters;
INFO  : Compiling command(queryId=hive_20171018091818_d8006afd-a1df-411f-a683-5a556a0f053f): GRANT ROLE writes TO GROUP inserters
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171018091818_d8006afd-a1df-411f-a683-5a556a0f053f); Time taken: 0.062 seconds
INFO  : Executing command(queryId=hive_20171018091818_d8006afd-a1df-411f-a683-5a556a0f053f): GRANT ROLE writes TO GROUP inserters
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171018091818_d8006afd-a1df-411f-a683-5a556a0f053f); Time taken: 0.028 seconds
INFO  : OK
No rows affected (0.099 seconds)
```



### kinit as george, then login to beeline

kinit as george, login to beeline, and use SHOW TABLES;

```bash
$ kinit george
Password for george@ISHTARTEC.COM:
$ beeline
Beeline version 1.1.0-cdh5.8.3 by Apache Hive
beeline> !connect jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-24-43.eu-central-1.compute.internal@ISHTARTEC.COM
scan complete in 2ms
Connecting to jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-24-43.eu-central-1.compute.internal@ISHTARTEC.COM
Enter username for jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-24-43.eu-central-1.compute.internal@ISHTARTEC.COM: george
Enter password for jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-24-43.eu-central-1.compute.internal@ISHTARTEC.COM: ********
Connected to: Apache Hive (version 1.1.0-cdh5.8.3)
Driver: Hive JDBC (version 1.1.0-cdh5.8.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://localhost:10000/default> SHOW TABLES;
INFO  : Compiling command(queryId=hive_20171018092424_ef03deb9-8073-4fdb-9cb3-6c530390faab): SHOW TABLES
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20171018092424_ef03deb9-8073-4fdb-9cb3-6c530390faab); Time taken: 0.065 seconds
INFO  : Executing command(queryId=hive_20171018092424_ef03deb9-8073-4fdb-9cb3-6c530390faab): SHOW TABLES
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171018092424_ef03deb9-8073-4fdb-9cb3-6c530390faab); Time taken: 0.149 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0.337 seconds)
```

george should be able to see all tables


### Repeat the process as ferdinand

```bash
$ kinit ferdinand
Password for ferdinand@ISHTARTEC.COM:
$ klist
Ticket cache: FILE:/tmp/krb5cc_1001
Default principal: ferdinand@ISHTARTEC.COM

Valid starting       Expires              Service principal
10/18/2017 09:25:47  10/19/2017 09:25:47  krbtgt/ISHTARTEC.COM@ISHTARTEC.COM
	renew until 10/25/2017 09:25:47
$ beeline
Beeline version 1.1.0-cdh5.8.3 by Apache Hive
beeline> !connect jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-24-43.eu-central-1.compute.internal@ISHTARTEC.COM
scan complete in 3ms
Connecting to jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-24-43.eu-central-1.compute.internal@ISHTARTEC.COM
Enter username for jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-24-43.eu-central-1.compute.internal@ISHTARTEC.COM: ferdinand
Enter password for jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-24-43.eu-central-1.compute.internal@ISHTARTEC.COM: ********
Connected to: Apache Hive (version 1.1.0-cdh5.8.3)
Driver: Hive JDBC (version 1.1.0-cdh5.8.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://localhost:10000/default> SHOW TABLES;
INFO  : Compiling command(queryId=hive_20171018092626_93b441c2-b0f2-493f-9c8f-e774991f8404): SHOW TABLES
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20171018092626_93b441c2-b0f2-493f-9c8f-e774991f8404); Time taken: 0.068 seconds
INFO  : Executing command(queryId=hive_20171018092626_93b441c2-b0f2-493f-9c8f-e774991f8404): SHOW TABLES
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171018092626_93b441c2-b0f2-493f-9c8f-e774991f8404); Time taken: 0.132 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| sample_07  |
+------------+--+
1 row selected (0.316 seconds)
```

ferdinand should see sample_07