## Run the Hadoop pi program as the user siwicki

```bash
$ kinit
Password for siwicki@ISHTARTEC.CO.UK:
$ time hadoop jar /opt/cloudera/parcels/CDH/jars/hadoop-examples.jar pi 10 100
Number of Maps  = 10
Samples per Map = 100
Wrote input for Map #0
Wrote input for Map #1
Wrote input for Map #2
Wrote input for Map #3
Wrote input for Map #4
Wrote input for Map #5
Wrote input for Map #6
Wrote input for Map #7
Wrote input for Map #8
Wrote input for Map #9
Starting Job
17/10/20 05:05:51 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-17-59.eu-central-1.compute.internal/172.31.17.59:8032
17/10/20 05:05:51 INFO hdfs.DFSClient: Created token for siwicki: HDFS_DELEGATION_TOKEN owner=siwicki@ISHTARTEC.CO.UK, renewer=yarn, realUser=, issueDate=1508490351567, maxDate=1509095151567, sequenceNumber=2, masterKeyId=2 on 172.31.17.59:8020
17/10/20 05:05:51 INFO security.TokenCache: Got dt for hdfs://ip-172-31-17-59.eu-central-1.compute.internal:8020; Kind: HDFS_DELEGATION_TOKEN, Service: 172.31.17.59:8020, Ident: (token for siwicki: HDFS_DELEGATION_TOKEN owner=siwicki@ISHTARTEC.CO.UK, renewer=yarn, realUser=, issueDate=1508490351567, maxDate=1509095151567, sequenceNumber=2, masterKeyId=2)
17/10/20 05:05:51 INFO input.FileInputFormat: Total input paths to process : 10
17/10/20 05:05:51 INFO mapreduce.JobSubmitter: number of splits:10
17/10/20 05:05:51 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1508489865626_0002
17/10/20 05:05:51 INFO mapreduce.JobSubmitter: Kind: HDFS_DELEGATION_TOKEN, Service: 172.31.17.59:8020, Ident: (token for siwicki: HDFS_DELEGATION_TOKEN owner=siwicki@ISHTARTEC.CO.UK, renewer=yarn, realUser=, issueDate=1508490351567, maxDate=1509095151567, sequenceNumber=2, masterKeyId=2)
17/10/20 05:05:52 INFO impl.YarnClientImpl: Submitted application application_1508489865626_0002
17/10/20 05:05:52 INFO mapreduce.Job: The url to track the job: http://ip-172-31-17-59.eu-central-1.compute.internal:8088/proxy/application_1508489865626_0002/
17/10/20 05:05:52 INFO mapreduce.Job: Running job: job_1508489865626_0002
17/10/20 05:06:00 INFO mapreduce.Job: Job job_1508489865626_0002 running in uber mode : false
17/10/20 05:06:00 INFO mapreduce.Job:  map 0% reduce 0%
17/10/20 05:06:07 INFO mapreduce.Job:  map 20% reduce 0%
17/10/20 05:06:08 INFO mapreduce.Job:  map 30% reduce 0%
17/10/20 05:06:12 INFO mapreduce.Job:  map 60% reduce 0%
17/10/20 05:06:14 INFO mapreduce.Job:  map 100% reduce 0%
17/10/20 05:06:20 INFO mapreduce.Job:  map 100% reduce 100%
17/10/20 05:06:20 INFO mapreduce.Job: Job job_1508489865626_0002 completed successfully
17/10/20 05:06:20 INFO mapreduce.Job: Counters: 49
	File System Counters
		FILE: Number of bytes read=95
		FILE: Number of bytes written=1375919
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=3020
		HDFS: Number of bytes written=215
		HDFS: Number of read operations=43
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=3
	Job Counters
		Launched map tasks=10
		Launched reduce tasks=1
		Data-local map tasks=10
		Total time spent by all maps in occupied slots (ms)=93689
		Total time spent by all reduces in occupied slots (ms)=3208
		Total time spent by all map tasks (ms)=93689
		Total time spent by all reduce tasks (ms)=3208
		Total vcore-seconds taken by all map tasks=93689
		Total vcore-seconds taken by all reduce tasks=3208
		Total megabyte-seconds taken by all map tasks=95937536
		Total megabyte-seconds taken by all reduce tasks=3284992
	Map-Reduce Framework
		Map input records=10
		Map output records=20
		Map output bytes=180
		Map output materialized bytes=340
		Input split bytes=1840
		Combine input records=0
		Combine output records=0
		Reduce input groups=2
		Reduce shuffle bytes=340
		Reduce input records=20
		Reduce output records=0
		Spilled Records=40
		Shuffled Maps =10
		Failed Shuffles=0
		Merged Map outputs=10
		GC time elapsed (ms)=1649
		CPU time spent (ms)=8100
		Physical memory (bytes) snapshot=4618186752
		Virtual memory (bytes) snapshot=30698524672
		Total committed heap usage (bytes)=4911529984
	Shuffle Errors
		BAD_ID=0
		CONNECTION=0
		IO_ERROR=0
		WRONG_LENGTH=0
		WRONG_MAP=0
		WRONG_REDUCE=0
	File Input Format Counters
		Bytes Read=1180
	File Output Format Counters
		Bytes Written=97
Job Finished in 29.664 seconds
Estimated value of Pi is 3.14800000000000000000

real	0m32.607s
user	0m8.263s
sys	0m0.360s
```