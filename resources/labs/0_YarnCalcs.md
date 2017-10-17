
## YARN/RM Lab: Doing the Math

*Explain any adjustments you make in resources/labs/0_YARNCalcs.md*

Following the recommendations from:
http://www.cloudera.com/documentation/enterprise/latest/topics/cdh_ig_yarn_tuning.html

- The minimum memory for the OS could be 8GB. The spreadsheet formula for the OS considers a 10% and most of the OS are between 4-8GB. We could set a start point of 8GB.
- Impalad has been added with 32GB of RAM as it could be very memory intensive and 2 vCores.
- HBase has been added with 8GB for the Region Servers and 2 vCores.


*What criteria affects workload factor? What does a value of 1, 2, or 4 signify?*

When increasing the workload factor, the values of `mapreduce.job.reduces` and `-D mapreduce.job.maps` also increase until it reaches the value capped by `yarn.nodemanager.resource.cpu-vcores`, which is the number of available vcores for YARN resources (in green).

Set this factor based on the expected number of concurrent threads per core.  Use 1 for CPU intensive tasks up to 4 for standard I/O bound tasks.