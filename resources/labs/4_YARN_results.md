## YARN/RM Lab: Tuning for YARN

The tests have been done with the following parameters:

- 9 Mappers
- 1 Reducer
- Memory of 1024 and 2048 for Mappers and Reducers

The results for the `teragen` command between different tests are pretty much the same, probably because the bottleneck is on the network/disks due to the replication factor.

The big difference in time is on the `terasort` test. Increasing the ammount of RAM for Mappers and Reducers, decreases the maximum number of containers available and increases the time to complete the task.

The modified script runs this tests:

**Test 1:**

- 9 mappers
- 1 reducer
- 1024 MB of RAM

Results for `teragen`:
```bash
real	1m22.656s
user	0m5.914s
sys	0m0.303s
```

Results for `terasort`:
```bash
real	2m32.623s
user	0m8.145s
sys	0m0.331s
```

**Test 2:**

- 9 mappers
- 1 reducer
- 2048 MB of RAM

Results for `teragen`:
```bash
real	1m21.675s
user	0m6.019s
sys	0m0.267s
```

Results for `terasort`:
```bash
real	3m22.706s
user	0m8.730s
sys	0m0.368s
```

The full output of the `YARNtest.sh` script is:

```bash
+ MR=/opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce
+ HADOOP=/opt/cloudera/parcels/CDH/bin
++ date
+ echo Testing loop started on Tue Oct 17 09:21:15 EDT 2017
Testing loop started on Tue Oct 17 09:21:15 EDT 2017
+ for i in 9
+ for j in 1
+ for k in 1024 2048
++ echo '(1024*0.8)/1'
++ bc
+ MAP_MB=819
++ echo '(1024*0.8)/1'
++ bc
+ RED_MB=819
+ /opt/cloudera/parcels/CDH/bin/hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar teragen -Dmapreduce.job.maps=9 -Dmapreduce.map.memory.mb=1024 -Dmapreduce.map.java.opts.max.heap=819 51200000 results/tg-10GB-9-1-1024

real	1m22.656s
user	0m5.914s
sys	0m0.303s
+ /opt/cloudera/parcels/CDH/bin/hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar terasort -Dmapreduce.job.maps=9 -Dmapreduce.job.reduces=1 -Dmapreduce.map.memory.mb=1024 -Dmapreduce.map.java.opts.max.heap=819 -Dmapreduce.reduce.memory.mb=1024 -Dmapreduce.reduce.java.opts.max.heap=819 results/tg-10GB-9-1-1024 results/ts-10GB-9-1-1024

real	2m32.623s
user	0m8.145s
sys	0m0.331s
+ /opt/cloudera/parcels/CDH/bin/hadoop fs -rm -r -skipTrash results/tg-10GB-9-1-1024
Deleted results/tg-10GB-9-1-1024
+ /opt/cloudera/parcels/CDH/bin/hadoop fs -rm -r -skipTrash results/ts-10GB-9-1-1024
Deleted results/ts-10GB-9-1-1024
+ for k in 1024 2048
++ echo '(2048*0.8)/1'
++ bc
+ MAP_MB=1638
++ echo '(2048*0.8)/1'
++ bc
+ RED_MB=1638
+ /opt/cloudera/parcels/CDH/bin/hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar teragen -Dmapreduce.job.maps=9 -Dmapreduce.map.memory.mb=2048 -Dmapreduce.map.java.opts.max.heap=1638 51200000 results/tg-10GB-9-1-2048

real	1m21.675s
user	0m6.019s
sys	0m0.267s
+ /opt/cloudera/parcels/CDH/bin/hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar terasort -Dmapreduce.job.maps=9 -Dmapreduce.job.reduces=1 -Dmapreduce.map.memory.mb=2048 -Dmapreduce.map.java.opts.max.heap=1638 -Dmapreduce.reduce.memory.mb=2048 -Dmapreduce.reduce.java.opts.max.heap=1638 results/tg-10GB-9-1-2048 results/ts-10GB-9-1-2048

real	3m22.706s
user	0m8.730s
sys	0m0.368s
+ /opt/cloudera/parcels/CDH/bin/hadoop fs -rm -r -skipTrash results/tg-10GB-9-1-2048
Deleted results/tg-10GB-9-1-2048
+ /opt/cloudera/parcels/CDH/bin/hadoop fs -rm -r -skipTrash results/ts-10GB-9-1-2048
Deleted results/ts-10GB-9-1-2048
++ date
+ echo Testing loop ended on Tue Oct 17 09:30:04 EDT 2017
Testing loop ended on Tue Oct 17 09:30:04 EDT 2017
```
