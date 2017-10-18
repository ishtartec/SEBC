## Upgrade Cloudera Manager
### Use the API on the command line to:

- Report the latest available version of the API

```bash
$ curl -u ishtartec:cloudera 'http://localhost:7180/api/version'
v14
```

- Report the CM version

```bash
$ curl -u ishtartec:cloudera 'http://localhost:7180/api/v14/cm/version'
{
  "version" : "5.9.3",
  "buildUser" : "jenkins",
  "buildTimestamp" : "20170627-1506",
  "gitHash" : "23506bb4e114dd460bdac64c57a672e6be631907",
  "snapshot" : false
}
```

- List all CM users
```bash
$ curl -u ishtartec:cloudera 'http://localhost:7180/api/v14/users'
{
  "items" : [ {
    "name" : "admin",
    "roles" : [ "ROLE_LIMITED" ]
  }, {
    "name" : "ishtartec",
    "roles" : [ "ROLE_ADMIN" ]
  }, {
    "name" : "minotaur",
    "roles" : [ "ROLE_CONFIGURATOR" ]
  } ]
}
```

- Report the database server in use by CM

```bash
$ curl -u ishtartec:cloudera 'http://localhost:7180/api/v14/cm/scmDbInfo'
{
  "scmDbType" : "MYSQL",
  "embeddedDbUsed" : false
}
```