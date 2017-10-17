## HDFS Lab: Test HDFS Snapshots

 - Create a `precious` directory in HDFS; copy the ZIP course file into it.

```bash
$ hdfs dfs -mkdir precious
$ hdfs dfs -put SEBC-master.zip precious/
```
- Enable snapshots for precious

As the `hdfs` user:
```bash
$ hdfs dfsadmin -allowSnapshot /user/ishtartec/precious
Allowing snaphot on /user/ishtartec/precious succeeded
```

- Create a snapshot called `sebc-hdfs-test`

As the `ishtartec` user run:
```bash
$ hdfs dfs -createSnapshot /user/ishtartec/precious sebc-hdfs-test
Created snapshot /user/ishtartec/precious/.snapshot/sebc-hdfs-test
```

- Delete the directory
```bash
$ hdfs dfs -rm -r /user/ishtartec/precious
rm: Failed to move to trash: hdfs://ip-172-31-24-43.eu-central-1.compute.internal:8020/user/ishtartec/precious: The directory /user/ishtartec/precious cannot be deleted since /user/ishtartec/precious is snapshottable and already has snapshots
```

- Delete the ZIP file
```bash
$ hdfs dfs -rm -skipTrash /user/ishtartec/precious/SEBC-master.zip
Deleted /user/ishtartec/precious/SEBC-master.zip
```

- Restore the deleted file
```bash
$ hdfs dfs -cp /user/ishtartec/precious/.snapshot/sebc-hdfs-test/SEBC-master.zip /user/ishtartec/precious/
$ hdfs dfs -ls /user/ishtartec/precious/
Found 1 items
-rw-r--r--   3 ishtartec supergroup     450893 2017-10-17 05:25 /user/ishtartec/precious/SEBC-master.zip
```