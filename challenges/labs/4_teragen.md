## Put the following in the file challenges/labs/4_teragen.md

### The full teragen command

```bash
$ time hadoop jar /opt/cloudera/parcels/CDH/jars/hadoop-examples.jar teragen -Ddfs.blocksize=33554432 -Dmapreduce.job.maps=6 51200000 /user/ernest/tgen512m
```

## The output of the time command

```bash
[...]
	File Input Format Counters
		Bytes Read=0
	File Output Format Counters
		Bytes Written=5120000000

real	2m0.744s
user	0m7.411s
sys	0m0.324s
```

## The command and output of hdfs dfs -ls /user/ernest/tgen512m

```bash
$ hdfs dfs -ls /user/ernest/tgen512m
Found 7 items
-rw-r--r--   3 ernest ernest          0 2017-10-20 04:41 /user/ernest/tgen512m/_SUCCESS
-rw-r--r--   3 ernest ernest  853333400 2017-10-20 04:41 /user/ernest/tgen512m/part-m-00000
-rw-r--r--   3 ernest ernest  853333300 2017-10-20 04:41 /user/ernest/tgen512m/part-m-00001
-rw-r--r--   3 ernest ernest  853333300 2017-10-20 04:41 /user/ernest/tgen512m/part-m-00002
-rw-r--r--   3 ernest ernest  853333400 2017-10-20 04:41 /user/ernest/tgen512m/part-m-00003
-rw-r--r--   3 ernest ernest  853333300 2017-10-20 04:41 /user/ernest/tgen512m/part-m-00004
-rw-r--r--   3 ernest ernest  853333300 2017-10-20 04:41 /user/ernest/tgen512m/part-m-00005
```


## Show how many blocks are associated with this directory

```bash
$ hdfs fsck /user/ernest/tgen512m -blocks
Connecting to namenode via http://ip-172-31-17-59.eu-central-1.compute.internal:50070
FSCK started by root (auth:SIMPLE) from /172.31.17.59 for path /user/ernest/tgen512m at Fri Oct 20 04:43:31 EDT 2017
.......Status: HEALTHY
 Total size:	5120000000 B
 Total dirs:	1
 Total files:	7
 Total symlinks:		0
 Total blocks (validated):	156 (avg. block size 32820512 B)
 Minimally replicated blocks:	156 (100.0 %)
 Over-replicated blocks:	0 (0.0 %)
 Under-replicated blocks:	0 (0.0 %)
 Mis-replicated blocks:		0 (0.0 %)
 Default replication factor:	3
 Average block replication:	3.0
 Corrupt blocks:		0
 Missing replicas:		0 (0.0 %)
 Number of data-nodes:		3
 Number of racks:		1
FSCK ended at Fri Oct 20 04:43:31 EDT 2017 in 8 milliseconds


The filesystem under path '/user/ernest/tgen512m' is HEALTHY
```