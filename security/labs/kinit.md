## Lab: Integrating Kerberos with Cloudera Manager

Create a file `kinit.md` that includes:
- The `kinit` command you use to authenticate your test user
- The output from a `klist` command listing your credentials and ticket lifetime

`kinit`:
```bash
$ kinit ishtartec
Password for ishtartec@ISHTARTEC.COM:
```

`klist`:
```bash
$ klist
Ticket cache: FILE:/tmp/krb5cc_1001
Default principal: ishtartec@ISHTARTEC.COM

Valid starting       Expires              Service principal
10/18/2017 08:29:50  10/19/2017 08:29:50  krbtgt/ISHTARTEC.COM@ISHTARTEC.COM
	renew until 10/25/2017 08:29:50
```