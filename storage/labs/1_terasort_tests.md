## HDFS Lab: Test HDFS performance

### Create an end-user Linux account named with your GitHub handle:

On each host in the cluster:
```bash
$ useradd -d /home/ishtartec -m -s /bin/bash ishtartec
```

Now from one node create the HOME hdfs directory:

```bash
$ su - hdfs
$ hdfs dfs -mkdir /user/ishtartec
$ hdfs dfs -chown ishtartec /user/ishtartec
```

Run the following exercises as this user:
```bash
$ su - ishtartec
```

### Create a 10 GB file using `teragen`:

Using the following properties:

 - Set the number of mappers to four
 - Limit the block size to 32 MB
 - Land the result under your user's home directory
 - Use the time command to report the job's duration

```bash
$ time hadoop jar /opt/cloudera/parcels/CDH/jars/hadoop-examples.jar teragen -Ddfs.block.size=33554432 -Dmapred.map.tasks=4 107374182 /user/ishtartec/terasort-input
17/10/17 04:59:24 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-24-43.eu-central-1.compute.internal/172.31.24.43:8032
17/10/17 04:59:24 INFO terasort.TeraSort: Generating 107374182 using 4
17/10/17 04:59:25 INFO mapreduce.JobSubmitter: number of splits:4
17/10/17 04:59:25 INFO Configuration.deprecation: mapred.map.tasks is deprecated. Instead, use mapreduce.job.maps
17/10/17 04:59:25 INFO Configuration.deprecation: dfs.block.size is deprecated. Instead, use dfs.blocksize
17/10/17 04:59:25 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1508162258730_0004
17/10/17 04:59:26 INFO impl.YarnClientImpl: Submitted application application_1508162258730_0004
17/10/17 04:59:26 INFO mapreduce.Job: The url to track the job: http://ip-172-31-24-43.eu-central-1.compute.internal:8088/proxy/application_1508162258730_0004/
17/10/17 04:59:26 INFO mapreduce.Job: Running job: job_1508162258730_0004
17/10/17 04:59:31 INFO mapreduce.Job: Job job_1508162258730_0004 running in uber mode : false
17/10/17 04:59:31 INFO mapreduce.Job:  map 0% reduce 0%
17/10/17 04:59:42 INFO mapreduce.Job:  map 2% reduce 0%
17/10/17 04:59:43 INFO mapreduce.Job:  map 5% reduce 0%
17/10/17 04:59:44 INFO mapreduce.Job:  map 9% reduce 0%
17/10/17 04:59:45 INFO mapreduce.Job:  map 10% reduce 0%
17/10/17 04:59:46 INFO mapreduce.Job:  map 11% reduce 0%
17/10/17 04:59:47 INFO mapreduce.Job:  map 12% reduce 0%
17/10/17 04:59:49 INFO mapreduce.Job:  map 13% reduce 0%
17/10/17 04:59:50 INFO mapreduce.Job:  map 14% reduce 0%
17/10/17 04:59:51 INFO mapreduce.Job:  map 15% reduce 0%
17/10/17 04:59:53 INFO mapreduce.Job:  map 16% reduce 0%
17/10/17 04:59:54 INFO mapreduce.Job:  map 17% reduce 0%
17/10/17 04:59:55 INFO mapreduce.Job:  map 18% reduce 0%
17/10/17 04:59:56 INFO mapreduce.Job:  map 19% reduce 0%
17/10/17 04:59:58 INFO mapreduce.Job:  map 20% reduce 0%
17/10/17 04:59:59 INFO mapreduce.Job:  map 21% reduce 0%
17/10/17 05:00:01 INFO mapreduce.Job:  map 22% reduce 0%
17/10/17 05:00:02 INFO mapreduce.Job:  map 23% reduce 0%
17/10/17 05:00:04 INFO mapreduce.Job:  map 24% reduce 0%
17/10/17 05:00:05 INFO mapreduce.Job:  map 25% reduce 0%
17/10/17 05:00:07 INFO mapreduce.Job:  map 26% reduce 0%
17/10/17 05:00:08 INFO mapreduce.Job:  map 27% reduce 0%
17/10/17 05:00:10 INFO mapreduce.Job:  map 28% reduce 0%
17/10/17 05:00:11 INFO mapreduce.Job:  map 29% reduce 0%
17/10/17 05:00:13 INFO mapreduce.Job:  map 30% reduce 0%
17/10/17 05:00:14 INFO mapreduce.Job:  map 31% reduce 0%
17/10/17 05:00:16 INFO mapreduce.Job:  map 32% reduce 0%
17/10/17 05:00:17 INFO mapreduce.Job:  map 33% reduce 0%
17/10/17 05:00:18 INFO mapreduce.Job:  map 34% reduce 0%
17/10/17 05:00:20 INFO mapreduce.Job:  map 35% reduce 0%
17/10/17 05:00:22 INFO mapreduce.Job:  map 36% reduce 0%
17/10/17 05:00:23 INFO mapreduce.Job:  map 37% reduce 0%
17/10/17 05:00:25 INFO mapreduce.Job:  map 38% reduce 0%
17/10/17 05:00:27 INFO mapreduce.Job:  map 39% reduce 0%
17/10/17 05:00:29 INFO mapreduce.Job:  map 40% reduce 0%
17/10/17 05:00:30 INFO mapreduce.Job:  map 41% reduce 0%
17/10/17 05:00:32 INFO mapreduce.Job:  map 42% reduce 0%
17/10/17 05:00:33 INFO mapreduce.Job:  map 43% reduce 0%
17/10/17 05:00:34 INFO mapreduce.Job:  map 44% reduce 0%
17/10/17 05:00:36 INFO mapreduce.Job:  map 45% reduce 0%
17/10/17 05:00:37 INFO mapreduce.Job:  map 46% reduce 0%
17/10/17 05:00:39 INFO mapreduce.Job:  map 47% reduce 0%
17/10/17 05:00:40 INFO mapreduce.Job:  map 48% reduce 0%
17/10/17 05:00:42 INFO mapreduce.Job:  map 49% reduce 0%
17/10/17 05:00:45 INFO mapreduce.Job:  map 50% reduce 0%
17/10/17 05:00:46 INFO mapreduce.Job:  map 51% reduce 0%
17/10/17 05:00:48 INFO mapreduce.Job:  map 53% reduce 0%
17/10/17 05:00:49 INFO mapreduce.Job:  map 54% reduce 0%
17/10/17 05:00:51 INFO mapreduce.Job:  map 55% reduce 0%
17/10/17 05:00:52 INFO mapreduce.Job:  map 56% reduce 0%
17/10/17 05:00:54 INFO mapreduce.Job:  map 57% reduce 0%
17/10/17 05:00:55 INFO mapreduce.Job:  map 58% reduce 0%
17/10/17 05:00:57 INFO mapreduce.Job:  map 59% reduce 0%
17/10/17 05:00:58 INFO mapreduce.Job:  map 60% reduce 0%
17/10/17 05:01:00 INFO mapreduce.Job:  map 61% reduce 0%
17/10/17 05:01:01 INFO mapreduce.Job:  map 62% reduce 0%
17/10/17 05:01:03 INFO mapreduce.Job:  map 63% reduce 0%
17/10/17 05:01:04 INFO mapreduce.Job:  map 64% reduce 0%
17/10/17 05:01:06 INFO mapreduce.Job:  map 65% reduce 0%
17/10/17 05:01:07 INFO mapreduce.Job:  map 66% reduce 0%
17/10/17 05:01:09 INFO mapreduce.Job:  map 67% reduce 0%
17/10/17 05:01:10 INFO mapreduce.Job:  map 68% reduce 0%
17/10/17 05:01:12 INFO mapreduce.Job:  map 69% reduce 0%
17/10/17 05:01:13 INFO mapreduce.Job:  map 70% reduce 0%
17/10/17 05:01:15 INFO mapreduce.Job:  map 71% reduce 0%
17/10/17 05:01:16 INFO mapreduce.Job:  map 72% reduce 0%
17/10/17 05:01:18 INFO mapreduce.Job:  map 73% reduce 0%
17/10/17 05:01:19 INFO mapreduce.Job:  map 74% reduce 0%
17/10/17 05:01:21 INFO mapreduce.Job:  map 76% reduce 0%
17/10/17 05:01:22 INFO mapreduce.Job:  map 77% reduce 0%
17/10/17 05:01:24 INFO mapreduce.Job:  map 78% reduce 0%
17/10/17 05:01:27 INFO mapreduce.Job:  map 79% reduce 0%
17/10/17 05:01:28 INFO mapreduce.Job:  map 80% reduce 0%
17/10/17 05:01:30 INFO mapreduce.Job:  map 82% reduce 0%
17/10/17 05:01:31 INFO mapreduce.Job:  map 83% reduce 0%
17/10/17 05:01:34 INFO mapreduce.Job:  map 84% reduce 0%
17/10/17 05:01:36 INFO mapreduce.Job:  map 86% reduce 0%
17/10/17 05:01:37 INFO mapreduce.Job:  map 87% reduce 0%
17/10/17 05:01:39 INFO mapreduce.Job:  map 88% reduce 0%
17/10/17 05:01:42 INFO mapreduce.Job:  map 89% reduce 0%
17/10/17 05:01:43 INFO mapreduce.Job:  map 90% reduce 0%
17/10/17 05:01:45 INFO mapreduce.Job:  map 91% reduce 0%
17/10/17 05:01:48 INFO mapreduce.Job:  map 93% reduce 0%
17/10/17 05:01:49 INFO mapreduce.Job:  map 94% reduce 0%
17/10/17 05:01:51 INFO mapreduce.Job:  map 95% reduce 0%
17/10/17 05:01:52 INFO mapreduce.Job:  map 96% reduce 0%
17/10/17 05:01:54 INFO mapreduce.Job:  map 97% reduce 0%
17/10/17 05:01:57 INFO mapreduce.Job:  map 99% reduce 0%
17/10/17 05:02:00 INFO mapreduce.Job:  map 100% reduce 0%
17/10/17 05:02:00 INFO mapreduce.Job: Job job_1508162258730_0004 completed successfully
17/10/17 05:02:00 INFO mapreduce.Job: Counters: 31
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=488708
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=344
		HDFS: Number of bytes written=10737418200
		HDFS: Number of read operations=16
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=8
	Job Counters
		Launched map tasks=4
		Other local map tasks=4
		Total time spent by all maps in occupied slots (ms)=577879
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=577879
		Total vcore-seconds taken by all map tasks=577879
		Total megabyte-seconds taken by all map tasks=591748096
	Map-Reduce Framework
		Map input records=107374182
		Map output records=107374182
		Input split bytes=344
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=1940
		CPU time spent (ms)=173520
		Physical memory (bytes) snapshot=804433920
		Virtual memory (bytes) snapshot=6313353216
		Total committed heap usage (bytes)=786432000
	org.apache.hadoop.examples.terasort.TeraGen$Counters
		CHECKSUM=230593859918397906
	File Input Format Counters
		Bytes Read=0
	File Output Format Counters
		Bytes Written=10737418200

real	2m39.147s
user	0m6.183s
sys	0m0.309s
```

### Run the `terasort` command on this file:

 - Use the `time` command to report the job's duration
 - Land the result under your user's home directory

```bash
$ time hadoop jar /opt/cloudera/parcels/CDH/jars/hadoop-examples.jar terasort /user/ishtartec/terasort-input /user/ishtartec/terasort-output
17/10/17 05:05:02 INFO terasort.TeraSort: starting
17/10/17 05:05:04 INFO input.FileInputFormat: Total input paths to process : 4
Spent 288ms computing base-splits.
Spent 7ms computing TeraScheduler splits.
Computing input splits took 297ms
Sampling 10 splits of 320
Making 6 from 100000 sampled records
Computing parititions took 821ms
Spent 1120ms computing partitions.
17/10/17 05:05:05 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-24-43.eu-central-1.compute.internal/172.31.24.43:8032
17/10/17 05:05:05 INFO mapreduce.JobSubmitter: number of splits:320
17/10/17 05:05:05 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1508162258730_0005
17/10/17 05:05:05 INFO impl.YarnClientImpl: Submitted application application_1508162258730_0005
17/10/17 05:05:05 INFO mapreduce.Job: The url to track the job: http://ip-172-31-24-43.eu-central-1.compute.internal:8088/proxy/application_1508162258730_0005/
17/10/17 05:05:05 INFO mapreduce.Job: Running job: job_1508162258730_0005
17/10/17 05:05:12 INFO mapreduce.Job: Job job_1508162258730_0005 running in uber mode : false
17/10/17 05:05:12 INFO mapreduce.Job:  map 0% reduce 0%
17/10/17 05:05:23 INFO mapreduce.Job:  map 2% reduce 0%
17/10/17 05:05:26 INFO mapreduce.Job:  map 3% reduce 0%
17/10/17 05:05:33 INFO mapreduce.Job:  map 4% reduce 0%
17/10/17 05:05:34 INFO mapreduce.Job:  map 5% reduce 0%
17/10/17 05:05:39 INFO mapreduce.Job:  map 6% reduce 0%
17/10/17 05:05:40 INFO mapreduce.Job:  map 7% reduce 0%
17/10/17 05:05:44 INFO mapreduce.Job:  map 8% reduce 0%
17/10/17 05:05:49 INFO mapreduce.Job:  map 9% reduce 0%
17/10/17 05:05:53 INFO mapreduce.Job:  map 10% reduce 0%
17/10/17 05:05:54 INFO mapreduce.Job:  map 11% reduce 0%
17/10/17 05:06:00 INFO mapreduce.Job:  map 12% reduce 0%
17/10/17 05:06:03 INFO mapreduce.Job:  map 13% reduce 0%
17/10/17 05:06:05 INFO mapreduce.Job:  map 14% reduce 0%
17/10/17 05:06:08 INFO mapreduce.Job:  map 15% reduce 0%
17/10/17 05:06:13 INFO mapreduce.Job:  map 16% reduce 0%
17/10/17 05:06:15 INFO mapreduce.Job:  map 17% reduce 0%
17/10/17 05:06:17 INFO mapreduce.Job:  map 18% reduce 0%
17/10/17 05:06:22 INFO mapreduce.Job:  map 19% reduce 0%
17/10/17 05:06:25 INFO mapreduce.Job:  map 20% reduce 0%
17/10/17 05:06:28 INFO mapreduce.Job:  map 21% reduce 0%
17/10/17 05:06:30 INFO mapreduce.Job:  map 22% reduce 0%
17/10/17 05:06:35 INFO mapreduce.Job:  map 23% reduce 0%
17/10/17 05:06:38 INFO mapreduce.Job:  map 24% reduce 0%
17/10/17 05:06:42 INFO mapreduce.Job:  map 25% reduce 0%
17/10/17 05:06:44 INFO mapreduce.Job:  map 26% reduce 0%
17/10/17 05:06:48 INFO mapreduce.Job:  map 27% reduce 0%
17/10/17 05:06:53 INFO mapreduce.Job:  map 28% reduce 0%
17/10/17 05:06:54 INFO mapreduce.Job:  map 29% reduce 0%
17/10/17 05:06:56 INFO mapreduce.Job:  map 30% reduce 0%
17/10/17 05:07:02 INFO mapreduce.Job:  map 31% reduce 0%
17/10/17 05:07:04 INFO mapreduce.Job:  map 32% reduce 0%
17/10/17 05:07:07 INFO mapreduce.Job:  map 33% reduce 0%
17/10/17 05:07:12 INFO mapreduce.Job:  map 34% reduce 0%
17/10/17 05:07:14 INFO mapreduce.Job:  map 35% reduce 0%
17/10/17 05:07:17 INFO mapreduce.Job:  map 36% reduce 0%
17/10/17 05:07:20 INFO mapreduce.Job:  map 37% reduce 0%
17/10/17 05:07:23 INFO mapreduce.Job:  map 38% reduce 0%
17/10/17 05:07:29 INFO mapreduce.Job:  map 39% reduce 0%
17/10/17 05:07:32 INFO mapreduce.Job:  map 40% reduce 0%
17/10/17 05:07:34 INFO mapreduce.Job:  map 41% reduce 0%
17/10/17 05:07:37 INFO mapreduce.Job:  map 42% reduce 0%
17/10/17 05:07:42 INFO mapreduce.Job:  map 43% reduce 0%
17/10/17 05:07:43 INFO mapreduce.Job:  map 44% reduce 0%
17/10/17 05:07:48 INFO mapreduce.Job:  map 45% reduce 0%
17/10/17 05:07:51 INFO mapreduce.Job:  map 46% reduce 0%
17/10/17 05:07:55 INFO mapreduce.Job:  map 47% reduce 0%
17/10/17 05:07:57 INFO mapreduce.Job:  map 48% reduce 0%
17/10/17 05:08:00 INFO mapreduce.Job:  map 49% reduce 0%
17/10/17 05:08:04 INFO mapreduce.Job:  map 50% reduce 0%
17/10/17 05:08:07 INFO mapreduce.Job:  map 51% reduce 0%
17/10/17 05:08:10 INFO mapreduce.Job:  map 52% reduce 0%
17/10/17 05:08:13 INFO mapreduce.Job:  map 53% reduce 0%
17/10/17 05:08:19 INFO mapreduce.Job:  map 54% reduce 0%
17/10/17 05:08:21 INFO mapreduce.Job:  map 55% reduce 0%
17/10/17 05:08:23 INFO mapreduce.Job:  map 56% reduce 0%
17/10/17 05:08:25 INFO mapreduce.Job:  map 57% reduce 0%
17/10/17 05:08:32 INFO mapreduce.Job:  map 58% reduce 0%
17/10/17 05:08:34 INFO mapreduce.Job:  map 59% reduce 0%
17/10/17 05:08:35 INFO mapreduce.Job:  map 60% reduce 0%
17/10/17 05:08:41 INFO mapreduce.Job:  map 61% reduce 0%
17/10/17 05:08:43 INFO mapreduce.Job:  map 62% reduce 0%
17/10/17 05:08:47 INFO mapreduce.Job:  map 63% reduce 0%
17/10/17 05:08:50 INFO mapreduce.Job:  map 64% reduce 0%
17/10/17 05:08:53 INFO mapreduce.Job:  map 65% reduce 0%
17/10/17 05:08:57 INFO mapreduce.Job:  map 66% reduce 0%
17/10/17 05:08:59 INFO mapreduce.Job:  map 67% reduce 0%
17/10/17 05:09:02 INFO mapreduce.Job:  map 68% reduce 0%
17/10/17 05:09:07 INFO mapreduce.Job:  map 69% reduce 0%
17/10/17 05:09:11 INFO mapreduce.Job:  map 70% reduce 0%
17/10/17 05:09:12 INFO mapreduce.Job:  map 71% reduce 0%
17/10/17 05:09:15 INFO mapreduce.Job:  map 72% reduce 0%
17/10/17 05:09:20 INFO mapreduce.Job:  map 73% reduce 0%
17/10/17 05:09:23 INFO mapreduce.Job:  map 74% reduce 0%
17/10/17 05:09:24 INFO mapreduce.Job:  map 75% reduce 0%
17/10/17 05:09:30 INFO mapreduce.Job:  map 76% reduce 0%
17/10/17 05:09:32 INFO mapreduce.Job:  map 77% reduce 0%
17/10/17 05:09:37 INFO mapreduce.Job:  map 78% reduce 0%
17/10/17 05:09:40 INFO mapreduce.Job:  map 79% reduce 0%
17/10/17 05:09:41 INFO mapreduce.Job:  map 80% reduce 0%
17/10/17 05:09:48 INFO mapreduce.Job:  map 81% reduce 0%
17/10/17 05:09:50 INFO mapreduce.Job:  map 82% reduce 0%
17/10/17 05:09:53 INFO mapreduce.Job:  map 83% reduce 0%
17/10/17 05:10:00 INFO mapreduce.Job:  map 83% reduce 5%
17/10/17 05:10:01 INFO mapreduce.Job:  map 83% reduce 6%
17/10/17 05:10:02 INFO mapreduce.Job:  map 84% reduce 6%
17/10/17 05:10:03 INFO mapreduce.Job:  map 84% reduce 9%
17/10/17 05:10:04 INFO mapreduce.Job:  map 84% reduce 11%
17/10/17 05:10:06 INFO mapreduce.Job:  map 84% reduce 13%
17/10/17 05:10:08 INFO mapreduce.Job:  map 85% reduce 13%
17/10/17 05:10:09 INFO mapreduce.Job:  map 85% reduce 15%
17/10/17 05:10:10 INFO mapreduce.Job:  map 85% reduce 16%
17/10/17 05:10:12 INFO mapreduce.Job:  map 85% reduce 19%
17/10/17 05:10:13 INFO mapreduce.Job:  map 86% reduce 21%
17/10/17 05:10:16 INFO mapreduce.Job:  map 86% reduce 22%
17/10/17 05:10:19 INFO mapreduce.Job:  map 87% reduce 23%
17/10/17 05:10:22 INFO mapreduce.Job:  map 87% reduce 24%
17/10/17 05:10:23 INFO mapreduce.Job:  map 88% reduce 24%
17/10/17 05:10:29 INFO mapreduce.Job:  map 89% reduce 24%
17/10/17 05:10:30 INFO mapreduce.Job:  map 89% reduce 25%
17/10/17 05:10:34 INFO mapreduce.Job:  map 90% reduce 25%
17/10/17 05:10:37 INFO mapreduce.Job:  map 91% reduce 25%
17/10/17 05:10:42 INFO mapreduce.Job:  map 92% reduce 25%
17/10/17 05:10:46 INFO mapreduce.Job:  map 92% reduce 26%
17/10/17 05:10:48 INFO mapreduce.Job:  map 93% reduce 26%
17/10/17 05:10:51 INFO mapreduce.Job:  map 94% reduce 26%
17/10/17 05:10:56 INFO mapreduce.Job:  map 95% reduce 26%
17/10/17 05:11:00 INFO mapreduce.Job:  map 96% reduce 26%
17/10/17 05:11:02 INFO mapreduce.Job:  map 96% reduce 27%
17/10/17 05:11:04 INFO mapreduce.Job:  map 97% reduce 27%
17/10/17 05:11:10 INFO mapreduce.Job:  map 98% reduce 27%
17/10/17 05:11:14 INFO mapreduce.Job:  map 99% reduce 27%
17/10/17 05:11:18 INFO mapreduce.Job:  map 100% reduce 27%
17/10/17 05:11:19 INFO mapreduce.Job:  map 100% reduce 28%
17/10/17 05:11:22 INFO mapreduce.Job:  map 100% reduce 39%
17/10/17 05:11:23 INFO mapreduce.Job:  map 100% reduce 56%
17/10/17 05:11:25 INFO mapreduce.Job:  map 100% reduce 59%
17/10/17 05:11:26 INFO mapreduce.Job:  map 100% reduce 61%
17/10/17 05:11:28 INFO mapreduce.Job:  map 100% reduce 64%
17/10/17 05:11:29 INFO mapreduce.Job:  map 100% reduce 65%
17/10/17 05:11:31 INFO mapreduce.Job:  map 100% reduce 67%
17/10/17 05:11:32 INFO mapreduce.Job:  map 100% reduce 69%
17/10/17 05:11:34 INFO mapreduce.Job:  map 100% reduce 70%
17/10/17 05:11:35 INFO mapreduce.Job:  map 100% reduce 73%
17/10/17 05:11:37 INFO mapreduce.Job:  map 100% reduce 74%
17/10/17 05:11:38 INFO mapreduce.Job:  map 100% reduce 77%
17/10/17 05:11:40 INFO mapreduce.Job:  map 100% reduce 79%
17/10/17 05:11:41 INFO mapreduce.Job:  map 100% reduce 80%
17/10/17 05:11:43 INFO mapreduce.Job:  map 100% reduce 82%
17/10/17 05:11:44 INFO mapreduce.Job:  map 100% reduce 84%
17/10/17 05:11:46 INFO mapreduce.Job:  map 100% reduce 85%
17/10/17 05:11:47 INFO mapreduce.Job:  map 100% reduce 86%
17/10/17 05:11:50 INFO mapreduce.Job:  map 100% reduce 93%
17/10/17 05:11:53 INFO mapreduce.Job:  map 100% reduce 94%
17/10/17 05:11:56 INFO mapreduce.Job:  map 100% reduce 96%
17/10/17 05:11:59 INFO mapreduce.Job:  map 100% reduce 97%
17/10/17 05:12:02 INFO mapreduce.Job:  map 100% reduce 98%
17/10/17 05:12:05 INFO mapreduce.Job:  map 100% reduce 99%
17/10/17 05:12:08 INFO mapreduce.Job:  map 100% reduce 100%
17/10/17 05:12:12 INFO mapreduce.Job: Job job_1508162258730_0005 completed successfully
17/10/17 05:12:12 INFO mapreduce.Job: Counters: 49
	File System Counters
		FILE: Number of bytes read=4780809000
		FILE: Number of bytes written=9483917906
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=10737471000
		HDFS: Number of bytes written=10737418200
		HDFS: Number of read operations=978
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=12
	Job Counters
		Launched map tasks=320
		Launched reduce tasks=6
		Data-local map tasks=320
		Total time spent by all maps in occupied slots (ms)=2789647
		Total time spent by all reduces in occupied slots (ms)=649686
		Total time spent by all map tasks (ms)=2789647
		Total time spent by all reduce tasks (ms)=649686
		Total vcore-seconds taken by all map tasks=2789647
		Total vcore-seconds taken by all reduce tasks=649686
		Total megabyte-seconds taken by all map tasks=2856598528
		Total megabyte-seconds taken by all reduce tasks=665278464
	Map-Reduce Framework
		Map input records=107374182
		Map output records=107374182
		Map output bytes=10952166564
		Map output materialized bytes=4662784852
		Input split bytes=52800
		Combine input records=0
		Combine output records=0
		Reduce input groups=107374182
		Reduce shuffle bytes=4662784852
		Reduce input records=107374182
		Reduce output records=107374182
		Spilled Records=214748364
		Shuffled Maps =1920
		Failed Shuffles=0
		Merged Map outputs=1920
		GC time elapsed (ms)=41659
		CPU time spent (ms)=1595150
		Physical memory (bytes) snapshot=155829256192
		Virtual memory (bytes) snapshot=513749987328
		Total committed heap usage (bytes)=182899965952
	Shuffle Errors
		BAD_ID=0
		CONNECTION=0
		IO_ERROR=0
		WRONG_LENGTH=0
		WRONG_MAP=0
		WRONG_REDUCE=0
	File Input Format Counters
		Bytes Read=10737418200
	File Output Format Counters
		Bytes Written=10737418200
17/10/17 05:12:12 INFO terasort.TeraSort: done

real	7m11.400s
user	0m9.868s
sys	0m0.412s
```