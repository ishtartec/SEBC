## Use the API

Browse or use `curl` on the endpoint `./api/v2/cm/deployment`

```json
{
  "timestamp" : "2017-10-18T08:44:42.611Z",
  "clusters" : [ {
    "name" : "ishtartec",
    "version" : "CDH5",
    "services" : [ {
      "name" : "hive",
      "type" : "HIVE",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "HIVEMETASTORE",
          "items" : [ {
            "name" : "hive_metastore_java_heapsize",
            "value" : "593494016"
          } ]
        }, {
          "roleType" : "HIVESERVER2",
          "items" : [ {
            "name" : "hiveserver2_java_heapsize",
            "value" : "593494016"
          }, {
            "name" : "hiveserver2_spark_driver_memory",
            "value" : "966367641"
          }, {
            "name" : "hiveserver2_spark_executor_cores",
            "value" : "4"
          }, {
            "name" : "hiveserver2_spark_executor_memory",
            "value" : "3433247539"
          }, {
            "name" : "hiveserver2_spark_yarn_driver_memory_overhead",
            "value" : "102"
          }, {
            "name" : "hiveserver2_spark_yarn_executor_memory_overhead",
            "value" : "577"
          } ]
        } ],
        "items" : [ {
          "name" : "hive_metastore_database_host",
          "value" : "ip-172-31-24-43.eu-central-1.compute.internal"
        }, {
          "name" : "hive_metastore_database_password",
          "value" : "hive_password"
        }, {
          "name" : "mapreduce_yarn_service",
          "value" : "yarn"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hive-GATEWAY-628483fd744758cb69419afe34073cf9",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "b7f66e2b-d225-496c-90cc-b3b8d474cb37"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-777c49153bc78bc1a5c1dc7d040e9ece",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "990f2b27-fe4b-4d70-841e-6ac2e85b61f0"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-a321ab3648e41b091fcb74d2a8ad690d",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "9e0dab6a-e81c-4639-b472-9c00503aea3e"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-eed1ea27a340ab44c728735379138a2b",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "fdb4fe80-eec3-42d6-846d-23e2bc1969a8"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-f5dbc1d122156c46f027777a6ee8e643",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "0fd5e809-996f-4070-8213-597a869be6d4"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-HIVEMETASTORE-a321ab3648e41b091fcb74d2a8ad690d",
        "type" : "HIVEMETASTORE",
        "hostRef" : {
          "hostId" : "9e0dab6a-e81c-4639-b472-9c00503aea3e"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "9ieeovks4wbqdes63s28d0ahc"
          } ]
        }
      }, {
        "name" : "hive-HIVESERVER2-a321ab3648e41b091fcb74d2a8ad690d",
        "type" : "HIVESERVER2",
        "hostRef" : {
          "hostId" : "9e0dab6a-e81c-4639-b472-9c00503aea3e"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "8c7ihz4y4g6b598x1yh06dppv"
          } ]
        }
      } ],
      "displayName" : "Hive"
    }, {
      "name" : "zookeeper",
      "type" : "ZOOKEEPER",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "SERVER",
          "items" : [ {
            "name" : "zookeeper_server_java_heapsize",
            "value" : "593494016"
          } ]
        } ],
        "items" : [ ]
      },
      "roles" : [ {
        "name" : "zookeeper-SERVER-628483fd744758cb69419afe34073cf9",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "b7f66e2b-d225-496c-90cc-b3b8d474cb37"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "4blp5sen1ecv1igzydtitnsw4"
          }, {
            "name" : "serverId",
            "value" : "3"
          } ]
        }
      }, {
        "name" : "zookeeper-SERVER-a321ab3648e41b091fcb74d2a8ad690d",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "9e0dab6a-e81c-4639-b472-9c00503aea3e"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "8jjlmg1jvnfm3frjtgqs33rf6"
          }, {
            "name" : "serverId",
            "value" : "1"
          } ]
        }
      }, {
        "name" : "zookeeper-SERVER-f5dbc1d122156c46f027777a6ee8e643",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "0fd5e809-996f-4070-8213-597a869be6d4"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "3e748fh4mtp3nbx1h0uitvuky"
          }, {
            "name" : "serverId",
            "value" : "2"
          } ]
        }
      } ],
      "displayName" : "ZooKeeper"
    }, {
      "name" : "hue",
      "type" : "HUE",
      "config" : {
        "roleTypeConfigs" : [ ],
        "items" : [ {
          "name" : "database_host",
          "value" : "ip-172-31-24-43.eu-central-1.compute.internal"
        }, {
          "name" : "database_password",
          "value" : "huepassword"
        }, {
          "name" : "database_type",
          "value" : "mysql"
        }, {
          "name" : "hive_service",
          "value" : "hive"
        }, {
          "name" : "hue_webhdfs",
          "value" : "hdfs-HTTPFS-a321ab3648e41b091fcb74d2a8ad690d"
        }, {
          "name" : "oozie_service",
          "value" : "oozie"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hue-HUE_SERVER-a321ab3648e41b091fcb74d2a8ad690d",
        "type" : "HUE_SERVER",
        "hostRef" : {
          "hostId" : "9e0dab6a-e81c-4639-b472-9c00503aea3e"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "6vjg6rajj1cchkdnq6mdltgru"
          }, {
            "name" : "secret_key",
            "value" : "IeJZJrwUI2RmFcoDl8RmEuRVOSsI39"
          } ]
        }
      } ],
      "displayName" : "Hue"
    }, {
      "name" : "oozie",
      "type" : "OOZIE",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "OOZIE_SERVER",
          "items" : [ {
            "name" : "oozie_database_host",
            "value" : "ip-172-31-24-43.eu-central-1.compute.internal"
          }, {
            "name" : "oozie_database_password",
            "value" : "oozie"
          }, {
            "name" : "oozie_database_type",
            "value" : "mysql"
          }, {
            "name" : "oozie_database_user",
            "value" : "oozie"
          }, {
            "name" : "oozie_java_heapsize",
            "value" : "593494016"
          } ]
        } ],
        "items" : [ {
          "name" : "hive_service",
          "value" : "hive"
        }, {
          "name" : "mapreduce_yarn_service",
          "value" : "yarn"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "oozie-OOZIE_SERVER-a321ab3648e41b091fcb74d2a8ad690d",
        "type" : "OOZIE_SERVER",
        "hostRef" : {
          "hostId" : "9e0dab6a-e81c-4639-b472-9c00503aea3e"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "15p0beaamc6ptviffwtnxeuga"
          } ]
        }
      } ],
      "displayName" : "Oozie"
    }, {
      "name" : "yarn",
      "type" : "YARN",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "GATEWAY",
          "items" : [ {
            "name" : "mapred_reduce_tasks",
            "value" : "6"
          }, {
            "name" : "mapred_submit_replication",
            "value" : "1"
          } ]
        }, {
          "roleType" : "JOBHISTORY",
          "items" : [ {
            "name" : "mr2_jobhistory_java_heapsize",
            "value" : "593494016"
          } ]
        }, {
          "roleType" : "NODEMANAGER",
          "items" : [ {
            "name" : "rm_cpu_shares",
            "value" : "1800"
          }, {
            "name" : "rm_io_weight",
            "value" : "900"
          }, {
            "name" : "yarn_nodemanager_heartbeat_interval_ms",
            "value" : "100"
          }, {
            "name" : "yarn_nodemanager_local_dirs",
            "value" : "/disk1/yarn/nm"
          }, {
            "name" : "yarn_nodemanager_log_dirs",
            "value" : "/yarn/container-logs,/disk1/yarn/container-logs"
          }, {
            "name" : "yarn_nodemanager_resource_cpu_vcores",
            "value" : "3"
          }, {
            "name" : "yarn_nodemanager_resource_memory_mb",
            "value" : "4939"
          } ]
        }, {
          "roleType" : "RESOURCEMANAGER",
          "items" : [ {
            "name" : "resource_manager_java_heapsize",
            "value" : "593494016"
          }, {
            "name" : "yarn_scheduler_maximum_allocation_mb",
            "value" : "4939"
          }, {
            "name" : "yarn_scheduler_maximum_allocation_vcores",
            "value" : "3"
          } ]
        } ],
        "items" : [ {
          "name" : "hdfs_service",
          "value" : "hdfs"
        }, {
          "name" : "rm_dirty",
          "value" : "false"
        }, {
          "name" : "rm_last_allocation_percentage",
          "value" : "90"
        }, {
          "name" : "yarn_service_cgroups",
          "value" : "false"
        }, {
          "name" : "yarn_service_lce_always",
          "value" : "false"
        }, {
          "name" : "zk_authorization_secret_key",
          "value" : "3nIGtNKFewbUGuzasTuNXNjP3H3606"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "yarn-JOBHISTORY-a321ab3648e41b091fcb74d2a8ad690d",
        "type" : "JOBHISTORY",
        "hostRef" : {
          "hostId" : "9e0dab6a-e81c-4639-b472-9c00503aea3e"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "1jur8dq8p6nzrcy9os4hqsd9v"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-777c49153bc78bc1a5c1dc7d040e9ece",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "990f2b27-fe4b-4d70-841e-6ac2e85b61f0"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "jljez0h8h4c4s2f0oal4nu1e"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-eed1ea27a340ab44c728735379138a2b",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "fdb4fe80-eec3-42d6-846d-23e2bc1969a8"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "31elsn2j34lvyv88kxlklrd4n"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-f5dbc1d122156c46f027777a6ee8e643",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "0fd5e809-996f-4070-8213-597a869be6d4"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "417jhg1lb8fsp3ajwhq4xsogq"
          } ]
        }
      }, {
        "name" : "yarn-RESOURCEMANAGER-a321ab3648e41b091fcb74d2a8ad690d",
        "type" : "RESOURCEMANAGER",
        "hostRef" : {
          "hostId" : "9e0dab6a-e81c-4639-b472-9c00503aea3e"
        },
        "config" : {
          "items" : [ {
            "name" : "rm_id",
            "value" : "52"
          }, {
            "name" : "role_jceks_password",
            "value" : "8kq1p2y96r7ah649xq6p3t8a3"
          } ]
        }
      } ],
      "displayName" : "YARN (MR2 Included)"
    }, {
      "name" : "hdfs",
      "type" : "HDFS",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "BALANCER",
          "items" : [ {
            "name" : "balancer_java_heapsize",
            "value" : "593494016"
          } ]
        }, {
          "roleType" : "DATANODE",
          "items" : [ {
            "name" : "datanode_java_heapsize",
            "value" : "1073741824"
          }, {
            "name" : "dfs_data_dir_list",
            "value" : "/disk1/dfs/dn"
          }, {
            "name" : "dfs_datanode_du_reserved",
            "value" : "4293706956"
          }, {
            "name" : "dfs_datanode_max_locked_memory",
            "value" : "4294967296"
          }, {
            "name" : "rm_cpu_shares",
            "value" : "200"
          }, {
            "name" : "rm_io_weight",
            "value" : "100"
          } ]
        }, {
          "roleType" : "GATEWAY",
          "items" : [ {
            "name" : "dfs_client_use_trash",
            "value" : "true"
          } ]
        }, {
          "roleType" : "JOURNALNODE",
          "items" : [ {
            "name" : "dfs_journalnode_edits_dir",
            "value" : "/jn"
          } ]
        }, {
          "roleType" : "NAMENODE",
          "items" : [ {
            "name" : "dfs_name_dir_list",
            "value" : "/dfs/nn"
          }, {
            "name" : "dfs_namenode_servicerpc_address",
            "value" : "8022"
          }, {
            "name" : "namenode_java_heapsize",
            "value" : "593494016"
          } ]
        }, {
          "roleType" : "SECONDARYNAMENODE",
          "items" : [ {
            "name" : "fs_checkpoint_dir_list",
            "value" : "/dfs/snn"
          }, {
            "name" : "secondary_namenode_java_heapsize",
            "value" : "593494016"
          } ]
        } ],
        "items" : [ {
          "name" : "dfs_ha_fencing_cloudera_manager_secret_key",
          "value" : "8vUOLa2IbxsVcPEtP1YarpSOWnMtCr"
        }, {
          "name" : "dfs_ha_fencing_methods",
          "value" : "shell(true)"
        }, {
          "name" : "fc_authorization_secret_key",
          "value" : "DwuWkCTmLZpMLQxBDCEGZQY7oc2iz9"
        }, {
          "name" : "http_auth_signature_secret",
          "value" : "fRc5dp126MBJpKI8xnSpeEPWkziAFG"
        }, {
          "name" : "rm_dirty",
          "value" : "false"
        }, {
          "name" : "rm_last_allocation_percentage",
          "value" : "10"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hdfs-BALANCER-a321ab3648e41b091fcb74d2a8ad690d",
        "type" : "BALANCER",
        "hostRef" : {
          "hostId" : "9e0dab6a-e81c-4639-b472-9c00503aea3e"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hdfs-DATANODE-777c49153bc78bc1a5c1dc7d040e9ece",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "990f2b27-fe4b-4d70-841e-6ac2e85b61f0"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "e01mc82jclzukrlaj8yoou3x1"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-eed1ea27a340ab44c728735379138a2b",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "fdb4fe80-eec3-42d6-846d-23e2bc1969a8"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "ckacsgljalldn8ijartzyk916"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-f5dbc1d122156c46f027777a6ee8e643",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "0fd5e809-996f-4070-8213-597a869be6d4"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "7dfzoe0905lyp9neotl33bp29"
          } ]
        }
      }, {
        "name" : "hdfs-FAILOVERCONTROLLER-628483fd744758cb69419afe34073cf9",
        "type" : "FAILOVERCONTROLLER",
        "hostRef" : {
          "hostId" : "b7f66e2b-d225-496c-90cc-b3b8d474cb37"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "4nfu3sx4jvhm7bu6a6xkodtsk"
          } ]
        }
      }, {
        "name" : "hdfs-FAILOVERCONTROLLER-a321ab3648e41b091fcb74d2a8ad690d",
        "type" : "FAILOVERCONTROLLER",
        "hostRef" : {
          "hostId" : "9e0dab6a-e81c-4639-b472-9c00503aea3e"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "6oxjxdcl7buinugp58ihaxiai"
          } ]
        }
      }, {
        "name" : "hdfs-HTTPFS-a321ab3648e41b091fcb74d2a8ad690d",
        "type" : "HTTPFS",
        "hostRef" : {
          "hostId" : "9e0dab6a-e81c-4639-b472-9c00503aea3e"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "6itb2cy7qw9nyad1heau1hi0o"
          } ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-628483fd744758cb69419afe34073cf9",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "b7f66e2b-d225-496c-90cc-b3b8d474cb37"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "6vc1pt365hvapn9b68ezk3csr"
          } ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-a321ab3648e41b091fcb74d2a8ad690d",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "9e0dab6a-e81c-4639-b472-9c00503aea3e"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "8qu429bc4k3stedy6a0hojpu6"
          } ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-f5dbc1d122156c46f027777a6ee8e643",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "0fd5e809-996f-4070-8213-597a869be6d4"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "3bprz31gall59onwpi06lmysx"
          } ]
        }
      }, {
        "name" : "hdfs-NAMENODE-628483fd744758cb69419afe34073cf9",
        "type" : "NAMENODE",
        "hostRef" : {
          "hostId" : "b7f66e2b-d225-496c-90cc-b3b8d474cb37"
        },
        "config" : {
          "items" : [ {
            "name" : "autofailover_enabled",
            "value" : "true"
          }, {
            "name" : "dfs_federation_namenode_nameservice",
            "value" : "nameservice1"
          }, {
            "name" : "dfs_namenode_quorum_journal_name",
            "value" : "nameservice1"
          }, {
            "name" : "namenode_id",
            "value" : "60"
          }, {
            "name" : "role_jceks_password",
            "value" : "1ueywubtnkvf4smu8lqry640p"
          } ]
        }
      }, {
        "name" : "hdfs-NAMENODE-a321ab3648e41b091fcb74d2a8ad690d",
        "type" : "NAMENODE",
        "hostRef" : {
          "hostId" : "9e0dab6a-e81c-4639-b472-9c00503aea3e"
        },
        "config" : {
          "items" : [ {
            "name" : "autofailover_enabled",
            "value" : "true"
          }, {
            "name" : "dfs_federation_namenode_nameservice",
            "value" : "nameservice1"
          }, {
            "name" : "dfs_namenode_quorum_journal_name",
            "value" : "nameservice1"
          }, {
            "name" : "namenode_id",
            "value" : "54"
          }, {
            "name" : "role_jceks_password",
            "value" : "9jl73qx03f7or65gxrqfn5wbv"
          } ]
        }
      } ],
      "displayName" : "HDFS"
    } ]
  } ],
  "hosts" : [ {
    "hostId" : "fdb4fe80-eec3-42d6-846d-23e2bc1969a8",
    "ipAddress" : "172.31.22.96",
    "hostname" : "ip-172-31-22-96.eu-central-1.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "b7f66e2b-d225-496c-90cc-b3b8d474cb37",
    "ipAddress" : "172.31.24.128",
    "hostname" : "ip-172-31-24-128.eu-central-1.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "0fd5e809-996f-4070-8213-597a869be6d4",
    "ipAddress" : "172.31.24.243",
    "hostname" : "ip-172-31-24-243.eu-central-1.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "9e0dab6a-e81c-4639-b472-9c00503aea3e",
    "ipAddress" : "172.31.24.43",
    "hostname" : "ip-172-31-24-43.eu-central-1.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "990f2b27-fe4b-4d70-841e-6ac2e85b61f0",
    "ipAddress" : "172.31.26.192",
    "hostname" : "ip-172-31-26-192.eu-central-1.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  } ],
  "users" : [ {
    "name" : "__cloudera_internal_user__mgmt-ACTIVITYMONITOR-a321ab3648e41b091fcb74d2a8ad690d",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "aa49f7b8fb664e8fb9a44ad96a05c32323c811147b2ce99d5db683be9e81414c",
    "pwSalt" : -4786297363932554636,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-EVENTSERVER-a321ab3648e41b091fcb74d2a8ad690d",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "3cd8b9bfbc88c4df088c9e3577afa3cf72a4a76a83ef20337ca30bbaa379f934",
    "pwSalt" : -6232929181159792283,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-HOSTMONITOR-a321ab3648e41b091fcb74d2a8ad690d",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "78b13d159223b24644165401ed5450bb16f07f6c8ca049a3214cc27555d59222",
    "pwSalt" : -1060817141612196460,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-REPORTSMANAGER-a321ab3648e41b091fcb74d2a8ad690d",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "c132953084519be132db52af21af7b65c9e8a2310a488711872ccde515d1d21e",
    "pwSalt" : 4773527635603026304,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-SERVICEMONITOR-a321ab3648e41b091fcb74d2a8ad690d",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "27afcecaf514a1631b0b7328fba268af444ef007b6a843b282d48b34db2f2ae3",
    "pwSalt" : 2992256971526284460,
    "pwLogin" : true
  }, {
    "name" : "admin",
    "roles" : [ "ROLE_LIMITED" ],
    "pwHash" : "c881f3a2753e5e0013f1f1696cdd8ed2fa7c2b89d1257a56106ab675487cd4f5",
    "pwSalt" : -7906413883721630224,
    "pwLogin" : true
  }, {
    "name" : "ishtartec",
    "roles" : [ "ROLE_ADMIN" ],
    "pwHash" : "99c15e31c2790a235987b1988bbd8d0db6fd9477434912698244cef8db1271a6",
    "pwSalt" : 3476692175886662183,
    "pwLogin" : true
  }, {
    "name" : "minotaur",
    "roles" : [ "ROLE_CONFIGURATOR" ],
    "pwHash" : "8d86ed655c5bc835cd3bec96f6635bc18351c4e739d5174fed6491608b0e43f8",
    "pwSalt" : -9077296665857867056,
    "pwLogin" : true
  } ],
  "versionInfo" : {
    "version" : "5.8.3",
    "buildUser" : "jenkins",
    "buildTimestamp" : "20161019-1013",
    "gitHash" : "518f0d6d44abc87bc392646e4369a20c8192b7cf",
    "snapshot" : false
  },
  "managementService" : {
    "name" : "mgmt",
    "type" : "MGMT",
    "config" : {
      "roleTypeConfigs" : [ {
        "roleType" : "ACTIVITYMONITOR",
        "items" : [ {
          "name" : "firehose_database_host",
          "value" : "ip-172-31-24-43.eu-central-1.compute.internal"
        }, {
          "name" : "firehose_database_name",
          "value" : "amon"
        }, {
          "name" : "firehose_database_password",
          "value" : "amon_password"
        }, {
          "name" : "firehose_database_user",
          "value" : "amon"
        }, {
          "name" : "firehose_heapsize",
          "value" : "593494016"
        } ]
      }, {
        "roleType" : "EVENTSERVER",
        "items" : [ {
          "name" : "event_server_heapsize",
          "value" : "593494016"
        } ]
      }, {
        "roleType" : "HOSTMONITOR",
        "items" : [ {
          "name" : "firehose_heapsize",
          "value" : "593494016"
        }, {
          "name" : "firehose_non_java_memory_bytes",
          "value" : "805306368"
        } ]
      }, {
        "roleType" : "REPORTSMANAGER",
        "items" : [ {
          "name" : "headlamp_database_host",
          "value" : "ip-172-31-24-43.eu-central-1.compute.internal"
        }, {
          "name" : "headlamp_database_name",
          "value" : "rman"
        }, {
          "name" : "headlamp_database_password",
          "value" : "rman_password"
        }, {
          "name" : "headlamp_database_user",
          "value" : "rman"
        }, {
          "name" : "headlamp_heapsize",
          "value" : "593494016"
        } ]
      }, {
        "roleType" : "SERVICEMONITOR",
        "items" : [ {
          "name" : "firehose_heapsize",
          "value" : "593494016"
        }, {
          "name" : "firehose_non_java_memory_bytes",
          "value" : "805306368"
        } ]
      } ],
      "items" : [ ]
    },
    "roles" : [ {
      "name" : "mgmt-ACTIVITYMONITOR-a321ab3648e41b091fcb74d2a8ad690d",
      "type" : "ACTIVITYMONITOR",
      "hostRef" : {
        "hostId" : "9e0dab6a-e81c-4639-b472-9c00503aea3e"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "99ienoag8vkv2nigenyu0uxj6"
        } ]
      }
    }, {
      "name" : "mgmt-ALERTPUBLISHER-a321ab3648e41b091fcb74d2a8ad690d",
      "type" : "ALERTPUBLISHER",
      "hostRef" : {
        "hostId" : "9e0dab6a-e81c-4639-b472-9c00503aea3e"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "ah2m646f73k5f4afpltvl06rr"
        } ]
      }
    }, {
      "name" : "mgmt-EVENTSERVER-a321ab3648e41b091fcb74d2a8ad690d",
      "type" : "EVENTSERVER",
      "hostRef" : {
        "hostId" : "9e0dab6a-e81c-4639-b472-9c00503aea3e"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "ayooket0cub8rpmr22k00b1p8"
        } ]
      }
    }, {
      "name" : "mgmt-HOSTMONITOR-a321ab3648e41b091fcb74d2a8ad690d",
      "type" : "HOSTMONITOR",
      "hostRef" : {
        "hostId" : "9e0dab6a-e81c-4639-b472-9c00503aea3e"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "3kmlpl74h8c8erdy9ndztyk40"
        } ]
      }
    }, {
      "name" : "mgmt-REPORTSMANAGER-a321ab3648e41b091fcb74d2a8ad690d",
      "type" : "REPORTSMANAGER",
      "hostRef" : {
        "hostId" : "9e0dab6a-e81c-4639-b472-9c00503aea3e"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "5gaoigf3r29ecz63z68vr96gy"
        } ]
      }
    }, {
      "name" : "mgmt-SERVICEMONITOR-a321ab3648e41b091fcb74d2a8ad690d",
      "type" : "SERVICEMONITOR",
      "hostRef" : {
        "hostId" : "9e0dab6a-e81c-4639-b472-9c00503aea3e"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "4r3t5sp99tiq0e3uti8ao73rv"
        } ]
      }
    } ],
    "displayName" : "Cloudera Management Service"
  },
  "managerSettings" : {
    "items" : [ {
      "name" : "CLUSTER_STATS_START",
      "value" : "10/21/2012 17:10"
    }, {
      "name" : "PUBLIC_CLOUD_STATUS",
      "value" : "ON_PUBLIC_CLOUD"
    }, {
      "name" : "REMOTE_PARCEL_REPO_URLS",
      "value" : "http://ip-172-31-24-128.eu-central-1.compute.internal/cdh5.8.3/,https://archive.cloudera.com/cdh4/parcels/latest/,https://archive.cloudera.com/impala/parcels/latest/,https://archive.cloudera.com/search/parcels/latest/,https://archive.cloudera.com/accumulo/parcels/1.4/,https://archive.cloudera.com/accumulo-c5/parcels/latest/,https://archive.cloudera.com/kafka/parcels/latest/,https://archive.cloudera.com/navigator-keytrustee5/parcels/latest/,https://archive.cloudera.com/spark/parcels/latest/,https://archive.cloudera.com/sqoop-connectors/parcels/latest/"
    } ]
  }
}
```