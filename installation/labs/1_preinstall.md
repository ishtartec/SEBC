
## OS Checks

### 1. Check vm.swappiness on all your nodes
On each host:

```bash
$ cat /proc/sys/vm/swappiness
30
```

The system is working with the *tuned* service. In order to set the swappiness level to 1, we need to execute on each host:

**Manually** change the swappiness:
```bash
$ sysctl vm.swappiness=1
```
Check the current tuned profile:
```bash
$ tuned-adm active
Current active profile: virtual-guest
```
Modify the vm.swappiness value in the current profile configuration file to make it permanent:
```bash
$ vi /usr/lib/tuned/virtual-guest/tuned.conf
vm.swappiness = 1
```

### 2. Show the mount attributes of all volumes

```bash
$ mount
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
devtmpfs on /dev type devtmpfs (rw,nosuid,size=7599292k,nr_inodes=1899823,mode=755)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,nodev,mode=755)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/usr/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/net_cls type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpuacct,cpu)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
configfs on /sys/kernel/config type configfs (rw,relatime)
/dev/xvda2 on / type xfs (rw,relatime,attr2,inode64,noquota)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=29,pgrp=1,timeout=300,minproto=5,maxproto=5,direct)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=1497296k,mode=700,uid=1000,gid=1000)
/dev/xvdf1 on /disk1 type ext4 (rw,noatime,data=ordered)
```

The **worker nodes** have a dedicated disk:

```bash
$ cat /etc/fstab
[...]
/dev/xvdf1	/disk1	ext4	defaults,noatime	0 0
```

### 3. Show the reserve space of any non-root, `ext`-based volumes


```bash
$ tune2fs -l /dev/xvdf1 | grep 'Reserved block count'
Reserved block count:     524275
```

We can reduce or disable the reserved space with the following command:

```bash
$ tune2fs -m 0 /dev/xvdf1
tune2fs 1.42.9 (28-Dec-2013)
Setting reserved blocks percentage to 0% (0 blocks)
$ tune2fs -l /dev/xvdf1 | grep 'Reserved block count'
Reserved block count:     0
```

### 4. Disable transparent hugepage support

On all nodes:

```bash
$ echo never > /sys/kernel/mm/transparent_hugepage/defrag
$ echo never > /sys/kernel/mm/transparent_hugepage/enabled
```

To make it permanent across reboots:
```bash
$ vi /etc/rc.local
[...]
echo never > /sys/kernel/mm/transparent_hugepage/defrag
echo never > /sys/kernel/mm/transparent_hugepage/enabled
```

Set executable permissions on rc.local file:
```bash
$ chmod +x /etc/rc.local
```

### 5. List your network interface configuration
It's the same configuration in all the nodes:

```bash
$ cat /etc/sysconfig/network-scripts/ifcfg-eth0
DEVICE="eth0"
BOOTPROTO="dhcp"
ONBOOT="yes"
TYPE="Ethernet"
USERCTL="yes"
PEERDNS="yes"
IPV6INIT="no"
```

Specifically for each node:

**Node 1:**
```bash
[root@ip-172-31-24-43 ec2-user]$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 9001 qdisc pfifo_fast state UP qlen 1000
    link/ether 02:40:c3:d9:a7:74 brd ff:ff:ff:ff:ff:ff
    inet 172.31.24.43/20 brd 172.31.31.255 scope global dynamic eth0
       valid_lft 2816sec preferred_lft 2816sec
```

**Node 2:**
```bash
[root@ip-172-31-24-128 ec2-user]$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 9001 qdisc pfifo_fast state UP qlen 1000
    link/ether 02:8a:28:e4:6e:98 brd ff:ff:ff:ff:ff:ff
    inet 172.31.24.128/20 brd 172.31.31.255 scope global dynamic eth0
       valid_lft 2233sec preferred_lft 2233sec
```

**Node 3:**
```bash
[root@ip-172-31-24-243 ec2-user]$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 9001 qdisc pfifo_fast state UP qlen 1000
    link/ether 02:f6:b6:78:cf:20 brd ff:ff:ff:ff:ff:ff
    inet 172.31.24.243/20 brd 172.31.31.255 scope global dynamic eth0
       valid_lft 2985sec preferred_lft 2985sec
```

**Node 4:**
```bash
[root@ip-172-31-26-192 ec2-user]$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 9001 qdisc pfifo_fast state UP qlen 1000
    link/ether 02:06:54:6f:32:2e brd ff:ff:ff:ff:ff:ff
    inet 172.31.26.192/20 brd 172.31.31.255 scope global dynamic eth0
       valid_lft 3185sec preferred_lft 3185sec
```

**Node 5:**
```bash
[root@ip-172-31-22-96 ec2-user]$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 9001 qdisc pfifo_fast state UP qlen 1000
    link/ether 02:f3:64:5f:89:ce brd ff:ff:ff:ff:ff:ff
    inet 172.31.22.96/20 brd 172.31.31.255 scope global dynamic eth0
       valid_lft 3340sec preferred_lft 3340sec
```

### 6. List forward and reverse host lookups using `getent` or `nslookup`

```bash
[root@ip-172-31-24-43 ec2-user]$ getent hosts ip-172-31-24-43.eu-central-1.compute.internal
172.31.24.43    ip-172-31-24-43.eu-central-1.compute.internal
[root@ip-172-31-24-43 ec2-user]$ getent hosts 172.31.24.43
172.31.24.43    ip-172-31-24-43.eu-central-1.compute.internal
[root@ip-172-31-24-43 ec2-user]$ getent hosts ip-172-31-24-128.eu-central-1.compute.internal
172.31.24.128   ip-172-31-24-128.eu-central-1.compute.internal
[root@ip-172-31-24-43 ec2-user]$ getent hosts 172.31.24.128
172.31.24.128   ip-172-31-24-128.eu-central-1.compute.internal
[root@ip-172-31-24-43 ec2-user]$ getent hosts ip-172-31-24-243.eu-central-1.compute.internal
172.31.24.243   ip-172-31-24-243.eu-central-1.compute.internal
[root@ip-172-31-24-43 ec2-user]$ getent hosts 172.31.24.243
172.31.24.243   ip-172-31-24-243.eu-central-1.compute.internal
[root@ip-172-31-24-43 ec2-user]$ getent hosts ip-172-31-26-192.eu-central-1.compute.internal
172.31.26.192   ip-172-31-26-192.eu-central-1.compute.internal
[root@ip-172-31-24-43 ec2-user]$ getent hosts 172.31.26.192
172.31.26.192   ip-172-31-26-192.eu-central-1.compute.internal
[root@ip-172-31-24-43 ec2-user]$ getent hosts ip-172-31-22-96.eu-central-1.compute.internal
172.31.22.96    ip-172-31-22-96.eu-central-1.compute.internal
[root@ip-172-31-24-43 ec2-user]$ getent hosts 172.31.22.96
172.31.22.96    ip-172-31-22-96.eu-central-1.compute.internal
```

### 7. Show the `nscd` service is running
The selected ami does not include the `nscd` service pre-installed:

```bash
$ ps -ef | grep nscd
root      1998  1969  0 05:56 pts/0    00:00:00 grep --color=auto nscd
# yum search nscd
Loaded plugins: amazon-id, rhui-lb, search-disabled-repos
=================================== N/S matched: nscd ===================================
nscd.x86_64 : A Name Service Caching Daemon (nscd).
```

Install `nscd`  from the repository on all nodes:

```bash
$ yum install -y nscd
$ systemctl enable nscd
Created symlink from /etc/systemd/system/multi-user.target.wants/nscd.service to /usr/lib/systemd/system/nscd.service.
Created symlink from /etc/systemd/system/sockets.target.wants/nscd.socket to /usr/lib/systemd/system/nscd.socket.
$ systemctl start nscd
$ ps -ef | grep nscd
nscd      2096     1  0 05:59 ?        00:00:00 /usr/sbin/nscd
```

### 8. Show the `ntpd` service is running

The selected version (RedHat 7.2) comes with `chronyd`. As requested by the instructions, we need to install `ntpd` on **each node**:

```bash
$ yum install -y ntp
$ systemctl enable ntpd
Created symlink from /etc/systemd/system/multi-user.target.wants/ntpd.service to /usr/lib/systemd/system/ntpd.service.
$ systemctl start ntpd
$ ps -ef | grep ntpd
ntp       9418     1  0 08:35 ?        00:00:00 /usr/sbin/ntpd -u ntp:ntp -g
```

We can also verify that the configuration file points to the RedHat servers:

```bash
$ cat /etc/ntp.conf
[...]
server 0.rhel.pool.ntp.org iburst
server 1.rhel.pool.ntp.org iburst
server 2.rhel.pool.ntp.org iburst
server 3.rhel.pool.ntp.org iburst
[...]
```

And check that is synchronized:
```bash
$ ntpstat
synchronised to NTP server (85.214.216.1) at stratum 4
   time correct to within 246 ms
   polling server every 64 s
```