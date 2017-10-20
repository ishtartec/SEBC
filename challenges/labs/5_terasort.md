## Run the terasort program as ernest using /user/ernest/tgen512m


```bash
$ time hadoop jar /opt/cloudera/parcels/CDH/jars/hadoop-examples.jar terasort /user/ernest/tgen512m /user/ernest/tgen512m-output
17/10/20 05:00:54 INFO terasort.TeraSort: starting
17/10/20 05:00:55 INFO hdfs.DFSClient: Created token for ernest: HDFS_DELEGATION_TOKEN owner=ernest@ISHTARTEC.CO.UK, renewer=yarn, realUser=, issueDate=1508490055313, maxDate=1509094855313, sequenceNumber=1, masterKeyId=2 on 172.31.17.59:8020
17/10/20 05:00:55 INFO security.TokenCache: Got dt for hdfs://ip-172-31-17-59.eu-central-1.compute.internal:8020; Kind: HDFS_DELEGATION_TOKEN, Service: 172.31.17.59:8020, Ident: (token for ernest: HDFS_DELEGATION_TOKEN owner=ernest@ISHTARTEC.CO.UK, renewer=yarn, realUser=, issueDate=1508490055313, maxDate=1509094855313, sequenceNumber=1, masterKeyId=2)
17/10/20 05:00:55 INFO input.FileInputFormat: Total input paths to process : 6
Spent 373ms computing base-splits.
Spent 3ms computing TeraScheduler splits.
Computing input splits took 377ms
Sampling 10 splits of 156
Making 6 from 100000 sampled records
Computing parititions took 735ms
Spent 1114ms computing partitions.
17/10/20 05:00:56 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-17-59.eu-central-1.compute.internal/172.31.17.59:8032
17/10/20 05:00:56 INFO mapreduce.JobSubmitter: number of splits:156
17/10/20 05:00:56 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1508489865626_0001
17/10/20 05:00:56 INFO mapreduce.JobSubmitter: Kind: HDFS_DELEGATION_TOKEN, Service: 172.31.17.59:8020, Ident: (token for ernest: HDFS_DELEGATION_TOKEN owner=ernest@ISHTARTEC.CO.UK, renewer=yarn, realUser=, issueDate=1508490055313, maxDate=1509094855313, sequenceNumber=1, masterKeyId=2)
17/10/20 05:00:58 INFO impl.YarnClientImpl: Submitted application application_1508489865626_0001
17/10/20 05:00:58 INFO mapreduce.Job: The url to track the job: http://ip-172-31-17-59.eu-central-1.compute.internal:8088/proxy/application_1508489865626_0001/
17/10/20 05:00:58 INFO mapreduce.Job: Running job: job_1508489865626_0001
17/10/20 05:01:07 INFO mapreduce.Job: Job job_1508489865626_0001 running in uber mode : false
17/10/20 05:01:07 INFO mapreduce.Job:  map 0% reduce 0%
17/10/20 05:01:18 INFO mapreduce.Job:  map 1% reduce 0%
17/10/20 05:01:19 INFO mapreduce.Job:  map 2% reduce 0%
17/10/20 05:01:22 INFO mapreduce.Job:  map 4% reduce 0%
17/10/20 05:01:26 INFO mapreduce.Job:  map 6% reduce 0%
17/10/20 05:01:28 INFO mapreduce.Job:  map 7% reduce 0%
17/10/20 05:01:29 INFO mapreduce.Job:  map 8% reduce 0%
17/10/20 05:01:32 INFO mapreduce.Job:  map 10% reduce 0%
17/10/20 05:01:35 INFO mapreduce.Job:  map 11% reduce 0%
17/10/20 05:01:37 INFO mapreduce.Job:  map 12% reduce 0%
17/10/20 05:01:38 INFO mapreduce.Job:  map 13% reduce 0%
17/10/20 05:01:40 INFO mapreduce.Job:  map 14% reduce 0%
17/10/20 05:01:41 INFO mapreduce.Job:  map 16% reduce 0%
17/10/20 05:01:42 INFO mapreduce.Job:  map 17% reduce 0%
17/10/20 05:01:47 INFO mapreduce.Job:  map 19% reduce 0%
17/10/20 05:01:50 INFO mapreduce.Job:  map 21% reduce 0%
17/10/20 05:01:51 INFO mapreduce.Job:  map 22% reduce 0%
17/10/20 05:01:52 INFO mapreduce.Job:  map 24% reduce 0%
17/10/20 05:01:56 INFO mapreduce.Job:  map 25% reduce 0%
17/10/20 05:01:59 INFO mapreduce.Job:  map 27% reduce 0%
17/10/20 05:02:00 INFO mapreduce.Job:  map 28% reduce 0%
17/10/20 05:02:02 INFO mapreduce.Job:  map 29% reduce 0%
17/10/20 05:02:03 INFO mapreduce.Job:  map 31% reduce 0%
17/10/20 05:02:07 INFO mapreduce.Job:  map 33% reduce 0%
17/10/20 05:02:09 INFO mapreduce.Job:  map 34% reduce 0%
17/10/20 05:02:12 INFO mapreduce.Job:  map 35% reduce 0%
17/10/20 05:02:13 INFO mapreduce.Job:  map 36% reduce 0%
17/10/20 05:02:15 INFO mapreduce.Job:  map 37% reduce 0%
17/10/20 05:02:16 INFO mapreduce.Job:  map 38% reduce 0%
17/10/20 05:02:17 INFO mapreduce.Job:  map 40% reduce 0%
17/10/20 05:02:20 INFO mapreduce.Job:  map 41% reduce 0%
17/10/20 05:02:22 INFO mapreduce.Job:  map 42% reduce 0%
17/10/20 05:02:25 INFO mapreduce.Job:  map 43% reduce 0%
17/10/20 05:02:26 INFO mapreduce.Job:  map 45% reduce 0%
17/10/20 05:02:27 INFO mapreduce.Job:  map 47% reduce 0%
17/10/20 05:02:30 INFO mapreduce.Job:  map 48% reduce 0%
17/10/20 05:02:33 INFO mapreduce.Job:  map 49% reduce 0%
17/10/20 05:02:35 INFO mapreduce.Job:  map 51% reduce 0%
17/10/20 05:02:37 INFO mapreduce.Job:  map 52% reduce 0%
17/10/20 05:02:38 INFO mapreduce.Job:  map 53% reduce 0%
17/10/20 05:02:39 INFO mapreduce.Job:  map 54% reduce 0%
17/10/20 05:02:41 INFO mapreduce.Job:  map 55% reduce 0%
17/10/20 05:02:44 INFO mapreduce.Job:  map 56% reduce 0%
17/10/20 05:02:45 INFO mapreduce.Job:  map 58% reduce 0%
17/10/20 05:02:46 INFO mapreduce.Job:  map 59% reduce 0%
17/10/20 05:02:49 INFO mapreduce.Job:  map 60% reduce 0%
17/10/20 05:02:50 INFO mapreduce.Job:  map 61% reduce 0%
17/10/20 05:02:51 INFO mapreduce.Job:  map 62% reduce 0%
17/10/20 05:02:52 INFO mapreduce.Job:  map 63% reduce 0%
17/10/20 05:02:55 INFO mapreduce.Job:  map 64% reduce 0%
17/10/20 05:02:56 INFO mapreduce.Job:  map 65% reduce 0%
17/10/20 05:02:58 INFO mapreduce.Job:  map 66% reduce 0%
17/10/20 05:03:00 INFO mapreduce.Job:  map 67% reduce 0%
17/10/20 05:03:02 INFO mapreduce.Job:  map 69% reduce 0%
17/10/20 05:03:03 INFO mapreduce.Job:  map 71% reduce 0%
17/10/20 05:03:06 INFO mapreduce.Job:  map 72% reduce 0%
17/10/20 05:03:08 INFO mapreduce.Job:  map 73% reduce 0%
17/10/20 05:03:10 INFO mapreduce.Job:  map 74% reduce 0%
17/10/20 05:03:11 INFO mapreduce.Job:  map 76% reduce 0%
17/10/20 05:03:14 INFO mapreduce.Job:  map 77% reduce 0%
17/10/20 05:03:15 INFO mapreduce.Job:  map 78% reduce 0%
17/10/20 05:03:17 INFO mapreduce.Job:  map 79% reduce 0%
17/10/20 05:03:19 INFO mapreduce.Job:  map 80% reduce 0%
17/10/20 05:03:20 INFO mapreduce.Job:  map 81% reduce 0%
17/10/20 05:03:21 INFO mapreduce.Job:  map 82% reduce 0%
17/10/20 05:03:22 INFO mapreduce.Job:  map 83% reduce 0%
17/10/20 05:03:25 INFO mapreduce.Job:  map 84% reduce 0%
17/10/20 05:03:26 INFO mapreduce.Job:  map 85% reduce 0%
17/10/20 05:03:27 INFO mapreduce.Job:  map 86% reduce 0%
17/10/20 05:03:29 INFO mapreduce.Job:  map 88% reduce 0%
17/10/20 05:03:32 INFO mapreduce.Job:  map 88% reduce 4%
17/10/20 05:03:35 INFO mapreduce.Job:  map 88% reduce 9%
17/10/20 05:03:36 INFO mapreduce.Job:  map 88% reduce 12%
17/10/20 05:03:37 INFO mapreduce.Job:  map 89% reduce 12%
17/10/20 05:03:38 INFO mapreduce.Job:  map 89% reduce 13%
17/10/20 05:03:39 INFO mapreduce.Job:  map 90% reduce 18%
17/10/20 05:03:41 INFO mapreduce.Job:  map 90% reduce 22%
17/10/20 05:03:42 INFO mapreduce.Job:  map 91% reduce 23%
17/10/20 05:03:43 INFO mapreduce.Job:  map 92% reduce 23%
17/10/20 05:03:44 INFO mapreduce.Job:  map 92% reduce 25%
17/10/20 05:03:46 INFO mapreduce.Job:  map 93% reduce 25%
17/10/20 05:03:47 INFO mapreduce.Job:  map 94% reduce 26%
17/10/20 05:03:50 INFO mapreduce.Job:  map 95% reduce 26%
17/10/20 05:03:52 INFO mapreduce.Job:  map 96% reduce 26%
17/10/20 05:03:53 INFO mapreduce.Job:  map 97% reduce 27%
17/10/20 05:03:56 INFO mapreduce.Job:  map 98% reduce 27%
17/10/20 05:03:57 INFO mapreduce.Job:  map 99% reduce 27%
17/10/20 05:03:58 INFO mapreduce.Job:  map 100% reduce 27%
17/10/20 05:03:59 INFO mapreduce.Job:  map 100% reduce 35%
17/10/20 05:04:00 INFO mapreduce.Job:  map 100% reduce 46%
17/10/20 05:04:02 INFO mapreduce.Job:  map 100% reduce 57%
17/10/20 05:04:03 INFO mapreduce.Job:  map 100% reduce 59%
17/10/20 05:04:05 INFO mapreduce.Job:  map 100% reduce 68%
17/10/20 05:04:06 INFO mapreduce.Job:  map 100% reduce 71%
17/10/20 05:04:08 INFO mapreduce.Job:  map 100% reduce 75%
17/10/20 05:04:09 INFO mapreduce.Job:  map 100% reduce 78%
17/10/20 05:04:12 INFO mapreduce.Job:  map 100% reduce 87%
17/10/20 05:04:13 INFO mapreduce.Job:  map 100% reduce 89%
17/10/20 05:04:15 INFO mapreduce.Job:  map 100% reduce 94%
17/10/20 05:04:18 INFO mapreduce.Job:  map 100% reduce 97%
17/10/20 05:04:20 INFO mapreduce.Job:  map 100% reduce 99%
17/10/20 05:04:21 INFO mapreduce.Job:  map 100% reduce 100%
17/10/20 05:04:27 INFO mapreduce.Job: Job job_1508489865626_0001 completed successfully
17/10/20 05:04:27 INFO mapreduce.Job: Counters: 49
	File System Counters
		FILE: Number of bytes read=2270958387
		FILE: Number of bytes written=4514842893
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=5120024336
		HDFS: Number of bytes written=5120000000
		HDFS: Number of read operations=486
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=12
	Job Counters
		Launched map tasks=156
		Launched reduce tasks=6
		Data-local map tasks=156
		Total time spent by all maps in occupied slots (ms)=1319754
		Total time spent by all reduces in occupied slots (ms)=288261
		Total time spent by all map tasks (ms)=1319754
		Total time spent by all reduce tasks (ms)=288261
		Total vcore-seconds taken by all map tasks=1319754
		Total vcore-seconds taken by all reduce tasks=288261
		Total megabyte-seconds taken by all map tasks=1351428096
		Total megabyte-seconds taken by all reduce tasks=295179264
	Map-Reduce Framework
		Map input records=51200000
		Map output records=51200000
		Map output bytes=5222400000
		Map output materialized bytes=2223497972
		Input split bytes=24336
		Combine input records=0
		Combine output records=0
		Reduce input groups=51200000
		Reduce shuffle bytes=2223497972
		Reduce input records=51200000
		Reduce output records=51200000
		Spilled Records=102400000
		Shuffled Maps =936
		Failed Shuffles=0
		Merged Map outputs=936
		GC time elapsed (ms)=32295
		CPU time spent (ms)=818520
		Physical memory (bytes) snapshot=79647346688
		Virtual memory (bytes) snapshot=452140425216
		Total committed heap usage (bytes)=83916488704
	Shuffle Errors
		BAD_ID=0
		CONNECTION=0
		IO_ERROR=0
		WRONG_LENGTH=0
		WRONG_MAP=0
		WRONG_REDUCE=0
	File Input Format Counters
		Bytes Read=5120000000
	File Output Format Counters
		Bytes Written=5120000000
17/10/20 05:04:27 INFO terasort.TeraSort: done

real	3m34.470s
user	0m10.676s
sys	0m0.399s
```