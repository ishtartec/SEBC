## Challenge 6 - Enable Sentry

### Login to beeline with the principal for `ernest`

List the result of `SHOW TABLES;` in `challenges/labs/6_results.md`

```bash
$ klist
Ticket cache: FILE:/tmp/krb5cc_2000
Default principal: ernest@ISHTARTEC.CO.UK

Valid starting       Expires              Service principal
10/20/2017 05:00:02  10/21/2017 05:00:02  krbtgt/ISHTARTEC.CO.UK@ISHTARTEC.CO.UK
	renew until 10/27/2017 05:00:02
$ beeline
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Beeline version 1.1.0-cdh5.9.3 by Apache Hive
beeline> !connect jdbc:hive2://ip-172-31-17-59.eu-central-1.compute.internal:10000/default;principal=hive/ip-172-31-17-59.eu-central-1.compute.internal@ISHTARTEC.CO.UK
scan complete in 3ms
Connecting to jdbc:hive2://ip-172-31-17-59.eu-central-1.compute.internal:10000/default;principal=hive/ip-172-31-17-59.eu-central-1.compute.internal@ISHTARTEC.CO.UK
Connected to: Apache Hive (version 1.1.0-cdh5.9.3)
Driver: Hive JDBC (version 1.1.0-cdh5.9.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-172-31-17-59.eu-central-1.> SHOW TABLES;
[...]
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0.326 seconds)
0: jdbc:hive2://ip-172-31-17-59.eu-central-1.>
```


### Login again to beeline as the principal for `siwicki`

List the result of `SHOW TABLES;` in the same file

```bash
$ klist
Ticket cache: FILE:/tmp/krb5cc_3000
Default principal: siwicki@ISHTARTEC.CO.UK

Valid starting       Expires              Service principal
10/20/2017 05:05:43  10/21/2017 05:05:43  krbtgt/ISHTARTEC.CO.UK@ISHTARTEC.CO.UK
	renew until 10/27/2017 05:05:43
$ beeline
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Beeline version 1.1.0-cdh5.9.3 by Apache Hive
beeline> !connect jdbc:hive2://ip-172-31-17-59.eu-central-1.compute.internal:10000/default;principal=hive/ip-172-31-17-59.eu-central-1.compute.internal@ISHTARTEC.CO.UK
scan complete in 2ms
[...]
0: jdbc:hive2://ip-172-31-17-59.eu-central-1.> SHOW TABLES;
INFO  : Compiling command(queryId=hive_20171020052929_1339e1cc-c877-4760-89d1-2e98dfdc6abe): SHOW TABLES
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20171020052929_1339e1cc-c877-4760-89d1-2e98dfdc6abe); Time taken: 0.056 seconds
INFO  : Executing command(queryId=hive_20171020052929_1339e1cc-c877-4760-89d1-2e98dfdc6abe): SHOW TABLES
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171020052929_1339e1cc-c877-4760-89d1-2e98dfdc6abe); Time taken: 0.16 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| sample_07  |
| sample_08  |
+------------+--+
2 rows selected (0.322 seconds)
0: jdbc:hive2://ip-172-31-17-59.eu-central-1.>
```