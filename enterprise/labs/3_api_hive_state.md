## Use the API

Write `curl` statements that stop, start, and check the current state of your Hive service.

**Stop the hive service:**
```bash
$ curl -X POST -u ishtartec:cloudera 'http://localhost:7180/api/v13/clusters/ishtartec/services/hive/commands/stop'
{
  "id" : 339,
  "name" : "Stop",
  "startTime" : "2017-10-18T08:58:29.825Z",
  "active" : true,
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  }
}
```


**Start the hive service:**
```bash
$ curl -X POST -u ishtartec:cloudera 'http://localhost:7180/api/v13/clusters/ishtartec/services/hive/commands/start'
{
  "id" : 343,
  "name" : "Start",
  "startTime" : "2017-10-18T09:02:25.308Z",
  "active" : true,
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  }
}
```

**Check the current state of the hive service:**
```bash
$ curl -u ishtartec:cloudera 'http://localhost:7180/api/v13/clusters/ishtartec/services/hive'
{
  "name" : "hive",
  "type" : "HIVE",
  "clusterRef" : {
    "clusterName" : "cluster"
  },
  "serviceUrl" : "http://ip-172-31-24-43.eu-central-1.compute.internal:7180/cmf/serviceRedirect/hive",
  "roleInstancesUrl" : "http://ip-172-31-24-43.eu-central-1.compute.internal:7180/cmf/serviceRedirect/hive/instances",
  "serviceState" : "STARTED",
  "healthSummary" : "GOOD",
  "healthChecks" : [ {
    "name" : "HIVE_HIVEMETASTORES_HEALTHY",
    "summary" : "GOOD",
    "suppressed" : false
  }, {
    "name" : "HIVE_HIVESERVER2S_HEALTHY",
    "summary" : "GOOD",
    "suppressed" : false
  } ],
  "configStalenessStatus" : "FRESH",
  "clientConfigStalenessStatus" : "FRESH",
  "maintenanceMode" : false,
  "maintenanceOwners" : [ ],
  "displayName" : "Hive",
  "entityStatus" : "GOOD_HEALTH"
```