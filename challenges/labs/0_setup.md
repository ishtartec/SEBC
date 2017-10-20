## Challenge Setup

 - List the cloud provider you are using (AWS, GCE, Azure, other)
 
	AWS on m3-xlarge
	
 - List the Linux release you have chosen

	RedHat EL 7.2
```	
hvm        |  RHEL-7.2_HVM-20161025-x86_64-1-Hourly2-GP2       |  ami-7def1712
```
	
 - Show that the disk space on each node is at least 30 GB

    It's the same setup for all nodes:

```bash
$ df -kh
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda2       40G  1.2G   39G   3% /
devtmpfs        7.3G     0  7.3G   0% /dev
tmpfs           7.2G     0  7.2G   0% /dev/shm
tmpfs           7.2G   17M  7.2G   1% /run
tmpfs           7.2G     0  7.2G   0% /sys/fs/cgroup
tmpfs           1.5G     0  1.5G   0% /run/user/1000
```

 - List the command and output for yum repolist enabled

```bash
$ yum repolist enabled
Loaded plugins: amazon-id, rhui-lb, search-disabled-repos
repo id                                          repo name                         status
rhui-REGION-client-config-server-7/x86_64        Red Hat Update Infrastructure 2.0      4
rhui-REGION-rhel-server-releases/7Server/x86_64  Red Hat Enterprise Linux Server 7 17,256
rhui-REGION-rhel-server-rh-common/7Server/x86_64 Red Hat Enterprise Linux Server 7    228
repolist: 17,488
```


### List the /etc/passwd entries for ernest and siwicki in your setup file

```bash
$ cat /etc/passwd
[...]
ernest:x:2000:2000::/home/ernest:/bin/bash
siwicki:x:3000:3000::/home/siwicki:/bin/bash
```

### List the /etc/group entries for usa and emea in your setup file

```bash
$ cat /etc/group
[...]
usa:x:3001:ernest
emea:x:3002:siwicki
```