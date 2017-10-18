## CM Monitoring Lab

 - *What is ubertask optimization?*

	The ubertask optimization runs "sufficiently small" jobs sequentially within a single JVM. "Small" is defined by the `mapreduce.job.ubertask.maxmaps`, `mapreduce.job.ubertask.maxreduces`, and `mapreduce.job.ubertask.maxbytes` settings.

	Using the parameter `mapreduce.job.ubertask.maxbytes` you can define the threshold for number of input bytes, beyond which a job is considered too big for ubertask optimization. If no value is specified, dfs.block.size is used as a default.

 - *Where in CM is the Kerberos Security Realm value displayed?*

	Administration —> Settings —> Security —> Kerberos Security Realm

 - *Which CDH service(s) host a property for
   enabling Kerberos authentication?*

	In Cloudera Manager, use the Search Bar with "enable kerberos" keywords. That will show the current installed services that will have the property to enable Kerberos authentication.

	In our current environment, this property appears at:

	 - Zookeeper
	 - Yarn (for http web consoles)
	 - HDFS (for http web consoles)

	As soon as you enable more services compatible with kerberos they will show in the search bar.

 - *How do you upgrade the CM agents?*

	After following the upgrade procedure for Cloudera Manager specified at https://www.cloudera.com/documentation/enterprise/latest/topics/cm_ag_ug_cm5.html (for your specific Cloudera Manager version), as described in **step 11** there are several ways to upgrade Cloudera Manager Agents, for example:

	 - Upgrade the Cloudera Manager Agent using Cloudera Manager
		 - When Cloudera Manager upgrades the Cloudera Manager agent, Cloudera Manager handles the upgrade and cleanup, and optionally upgrades the JDK.
		 - Select Yes, I would like to upgrade the Cloudera Manager Agent packages now and click Continue.
		 - Select the release of the Cloudera Manager Agent to install
		 - Specify credentials and initiate Agent installation
	 - Manually
   upgrading the packages
	   - On all cluster hosts except the Cloudera Manager Server host, stop the Agent
	   - Select No, I would like to skip the agent upgrade now and click Continue.
	   - Copy the repo file
	   - Upgrade the package using the specific method of the OS.
	   - On all cluster hosts, start the Agent



 - *Give the tsquery statement used to chart Hue's CPU utilization?*

```
SELECT cpu_system_rate + cpu_user_rate where category=ROLE and serviceName="hue"
```

 - Name all the roles that make up the Hive service
	 - Hive Metastore Server
	 - WebHCat Server
	 - HiveServer2
	 - Hive Gateway (for clients)

 - What steps must be completed before integrating Cloudera Manager with Kerberos?

	After selecting Administration --> Security and clicking on the Enable Kerberos button, it will display the steps required to Enable Kerberos:

	 - Set up a working KDC. Cloudera Manager supports MIT KDC and Active Directory.
	 - The KDC should be configured to have non-zero ticket lifetime and renewal lifetime. CDH will not work properly if tickets are not renewable.
	 - OpenLdap client libraries should be installed on the Cloudera Manager Server host if you want to use Active Directory. Also, Kerberos client libraries should be installed on ALL hosts.
	 - Cloudera Manager needs an account that has permissions to create other accounts in the KDC.
