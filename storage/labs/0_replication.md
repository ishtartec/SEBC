## HDFS Lab: Replicate to another cluster

We need to create the home directory of the ec2-user in HDFS before using teragen. As the ***hdfs*** user run:

```bash
$ hdfs dfs -mkdir /user/ec2-user
$ hdfs dfs -chown ec2-user /user/ec2-user
```

Then we create the source and target directory with my GitHub handle and my partner's GitHub handle:

```bash
$ hdfs dfs -mkdir /tmp/ishtartec
$ hdfs dfs -mkdir /tmp/rdelaros
````

### Use `teragen` to create a 500 MB file:

```bash
$ hadoop jar /opt/cloudera/parcels/CDH/jars/hadoop-examples.jar teragen -Dmapreduce.job.maps=1 5242880 /tmp/ishtartec/file500
17/10/17 04:25:17 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-24-43.eu-central-1.compute.internal/172.31.24.43:8032
17/10/17 04:25:17 INFO terasort.TeraSort: Generating 5242880 using 1
17/10/17 04:25:17 INFO mapreduce.JobSubmitter: number of splits:1
17/10/17 04:25:17 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1508162258730_0001
17/10/17 04:25:18 INFO impl.YarnClientImpl: Submitted application application_1508162258730_0001
17/10/17 04:25:18 INFO mapreduce.Job: The url to track the job: http://ip-172-31-24-43.eu-central-1.compute.internal:8088/proxy/application_1508162258730_0001/
17/10/17 04:25:18 INFO mapreduce.Job: Running job: job_1508162258730_0001
17/10/17 04:25:24 INFO mapreduce.Job: Job job_1508162258730_0001 running in uber mode : false
17/10/17 04:25:24 INFO mapreduce.Job:  map 0% reduce 0%
17/10/17 04:25:36 INFO mapreduce.Job:  map 87% reduce 0%
17/10/17 04:25:38 INFO mapreduce.Job:  map 100% reduce 0%
17/10/17 04:25:38 INFO mapreduce.Job: Job job_1508162258730_0001 completed successfully
17/10/17 04:25:38 INFO mapreduce.Job: Counters: 31
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=122162
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=82
		HDFS: Number of bytes written=524288000
		HDFS: Number of read operations=4
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=2
	Job Counters
		Launched map tasks=1
		Other local map tasks=1
		Total time spent by all maps in occupied slots (ms)=11436
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=11436
		Total vcore-seconds taken by all map tasks=11436
		Total megabyte-seconds taken by all map tasks=11710464
	Map-Reduce Framework
		Map input records=5242880
		Map output records=5242880
		Input split bytes=82
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=83
		CPU time spent (ms)=11380
		Physical memory (bytes) snapshot=357023744
		Virtual memory (bytes) snapshot=1571106816
		Total committed heap usage (bytes)=395837440
	org.apache.hadoop.examples.terasort.TeraGen$Counters
		CHECKSUM=11257830824958050
	File Input Format Counters
		Bytes Read=0
	File Output Format Counters
		Bytes Written=524288000
```

### Copy your partner's file to your target directory:

After opening port 14000 in the AWS Security Group:

```bash
$ hadoop distcp webhdfs://52.59.208.204:14000/tmp/rdelaros /tmp/rdelaros
```

### Browse the results:

For the source directory (`/tmp/ishtartec`):

```bash
$ hdfs fsck /tmp/ishtartec -files -blocks
Connecting to namenode via http://ip-172-31-24-43.eu-central-1.compute.internal:50070
FSCK started by ec2-user (auth:SIMPLE) from /172.31.24.43 for path /tmp/ishtartec at Tue Oct 17 04:37:30 EDT 2017
/tmp/ishtartec <dir>
/tmp/ishtartec/file500 <dir>
/tmp/ishtartec/file500/_SUCCESS 0 bytes, 0 block(s):  OK

/tmp/ishtartec/file500/part-m-00000 524288000 bytes, 4 block(s):  OK
0. BP-1945201565-172.31.24.43-1508162198061:blk_1073743616_2792 len=134217728 Live_repl=3
1. BP-1945201565-172.31.24.43-1508162198061:blk_1073743617_2793 len=134217728 Live_repl=3
2. BP-1945201565-172.31.24.43-1508162198061:blk_1073743618_2794 len=134217728 Live_repl=3
3. BP-1945201565-172.31.24.43-1508162198061:blk_1073743619_2795 len=121634816 Live_repl=3

Status: HEALTHY
 Total size:	524288000 B
 Total dirs:	2
 Total files:	2
 Total symlinks:		0
 Total blocks (validated):	4 (avg. block size 131072000 B)
 Minimally replicated blocks:	4 (100.0 %)
 Over-replicated blocks:	0 (0.0 %)
 Under-replicated blocks:	0 (0.0 %)
 Mis-replicated blocks:		0 (0.0 %)
 Default replication factor:	3
 Average block replication:	3.0
 Corrupt blocks:		0
 Missing replicas:		0 (0.0 %)
 Number of data-nodes:		3
 Number of racks:		1
FSCK ended at Tue Oct 17 04:37:30 EDT 2017 in 2 milliseconds


The filesystem under path '/tmp/ishtartec' is HEALTHY
```


For the target directory (`/tmp/rdelaros`):

```bash
$ hdfs fsck /tmp/rdelaros -files -blocks
Connecting to namenode via http://ip-172-31-24-43.eu-central-1.compute.internal:50070
FSCK started by ec2-user (auth:SIMPLE) from /172.31.24.43 for path /tmp/rdelaros at Tue Oct 17 04:38:51 EDT 2017
/tmp/rdelaros <dir>
/tmp/rdelaros/rdelaros <dir>
/tmp/rdelaros/rdelaros/teragen-500MB <dir>
/tmp/rdelaros/rdelaros/teragen-500MB/_SUCCESS 0 bytes, 0 block(s):  OK

/tmp/rdelaros/rdelaros/teragen-500MB/part-m-00000 524288000 bytes, 4 block(s):  OK
0. BP-1945201565-172.31.24.43-1508162198061:blk_1073743644_2820 len=134217728 Live_repl=3
1. BP-1945201565-172.31.24.43-1508162198061:blk_1073743646_2822 len=134217728 Live_repl=3
2. BP-1945201565-172.31.24.43-1508162198061:blk_1073743647_2823 len=134217728 Live_repl=3
3. BP-1945201565-172.31.24.43-1508162198061:blk_1073743648_2824 len=121634816 Live_repl=3

Status: HEALTHY
 Total size:	524288000 B
 Total dirs:	3
 Total files:	2
 Total symlinks:		0
 Total blocks (validated):	4 (avg. block size 131072000 B)
 Minimally replicated blocks:	4 (100.0 %)
 Over-replicated blocks:	0 (0.0 %)
 Under-replicated blocks:	0 (0.0 %)
 Mis-replicated blocks:		0 (0.0 %)
 Default replication factor:	3
 Average block replication:	3.0
 Corrupt blocks:		0
 Missing replicas:		0 (0.0 %)
 Number of data-nodes:		3
 Number of racks:		1
FSCK ended at Tue Oct 17 04:38:51 EDT 2017 in 2 milliseconds


The filesystem under path '/tmp/rdelaros' is HEALTHY
```
