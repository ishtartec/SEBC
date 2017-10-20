## List the command and output of ls /etc/yum.repos.d in challenges/labs/2_cm.md

```bash
$ ls /etc/yum.repos.d/
cloudera-manager.repo        redhat.repo                     rhui-load-balancers.conf
mysql-community.repo         redhat-rhui-client-config.repo
mysql-community-source.repo  redhat-rhui.repo
```

### Use the scm_prepare_database.sh script to write your db.properties file

```bash
$ /usr/share/cmf/schema/scm_prepare_database.sh mysql -h ip-172-31-25-233.eu-central-1.compute.internal --scm-host ip-172-31-17-59.eu-central-1.compute.internal scm scm scm
JAVA_HOME=/usr/java/jdk1.8.0_121
Verifying that we can write to /etc/cloudera-scm-server
Creating SCM configuration file in /etc/cloudera-scm-server
Executing:  /usr/java/jdk1.8.0_121/bin/java -cp /usr/share/java/mysql-connector-java.jar:/usr/share/java/oracle-connector-java.jar:/usr/share/cmf/schema/../lib/* com.cloudera.enterprise.dbutil.DbCommandExecutor /etc/cloudera-scm-server/db.properties com.cloudera.cmf.db.
[                          main] DbCommandExecutor              INFO  Successfully connected to database.
All done, your SCM database is configured correctly!
```