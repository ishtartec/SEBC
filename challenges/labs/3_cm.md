## Add the following to 3_cm.md

### Command and output for hdfs dfs -ls /user

```bash
$ hdfs dfs -ls /user
Found 8 items
drwxr-xr-x   - ec2-user ec2-user            0 2017-10-20 04:34 /user/ec2-user
drwxr-xr-x   - ernest   ernest              0 2017-10-20 04:31 /user/ernest
drwxr-xr-x   - hdfs     supergroup          0 2017-10-20 04:34 /user/hdfs
drwxrwxrwx   - mapred   hadoop              0 2017-10-20 04:29 /user/history
drwxrwxr-t   - hive     hive                0 2017-10-20 04:30 /user/hive
drwxrwxr-x   - hue      hue                 0 2017-10-20 04:30 /user/hue
drwxrwxr-x   - oozie    oozie               0 2017-10-20 04:31 /user/oozie
drwxr-xr-x   - siwicki  siwicki             0 2017-10-20 04:31 /user/siwicki
```

### The output from the CM API call ../api/v14/hosts

```json
{
  "items" : [ {
    "hostId" : "5fb691ba-a217-45f2-a8cb-b2589495b775",
    "ipAddress" : "172.31.17.59",
    "hostname" : "ip-172-31-17-59.eu-central-1.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-17-59.eu-central-1.compute.internal:7180/cmf/hostRedirect/5fb691ba-a217-45f2-a8cb-b2589495b775",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15332311040
  }, {
    "hostId" : "2557c361-1301-46c9-a518-9de9c42e3ef5",
    "ipAddress" : "172.31.25.233",
    "hostname" : "ip-172-31-25-233.eu-central-1.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-17-59.eu-central-1.compute.internal:7180/cmf/hostRedirect/2557c361-1301-46c9-a518-9de9c42e3ef5",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15332311040
  }, {
    "hostId" : "94cf816e-8a00-411e-9563-177b2d113de2",
    "ipAddress" : "172.31.26.177",
    "hostname" : "ip-172-31-26-177.eu-central-1.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-17-59.eu-central-1.compute.internal:7180/cmf/hostRedirect/94cf816e-8a00-411e-9563-177b2d113de2",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15332311040
  }, {
    "hostId" : "428fc8c3-1764-4a98-8698-dbf040a13c05",
    "ipAddress" : "172.31.27.207",
    "hostname" : "ip-172-31-27-207.eu-central-1.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-17-59.eu-central-1.compute.internal:7180/cmf/hostRedirect/428fc8c3-1764-4a98-8698-dbf040a13c05",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15332311040
  }, {
    "hostId" : "9d723298-dcce-47ab-bc30-2041ec45c048",
    "ipAddress" : "172.31.28.30",
    "hostname" : "ip-172-31-28-30.eu-central-1.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-17-59.eu-central-1.compute.internal:7180/cmf/hostRedirect/9d723298-dcce-47ab-bc30-2041ec45c048",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15332311040
  } ]
}
```