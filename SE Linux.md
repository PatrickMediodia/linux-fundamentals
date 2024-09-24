- security enhanced linux
- may `subject` do `action` on `object`
- modes
	- enforcing
		- enforces the loaded security policy on the entire system
	- permissive
		- acts like enforcing mode
		- but does not deny any operations
		- great for debugging
	- disabled
		- not recommended as it is hard to re-enable

- `/etc/selinux/config`
	- picked up on reboot
- `sestatus`
	- see detailed information about the se linux status
- `getenforce` - only get the selinux mode
- `setenforce 0/1` - not persistent

- changing the selinux mode on boot time
	- `enforcing=0` - system will boot into permissive mode
	- `selinux=0`
		- tells the kernel to not load any selinux components
		- causes an auto relabel on next reboot

```
a[[SE Linux]]usearch -c '<search string>' --raw | less 
grep '<search string>' /var/log/messages | less
ls -laZ <directory/file> // shows the selinux content for a file or directory
```

```
semanage fcontent -a -t <idk> <lol>
restorecon -Rv <dir>
```

`Lab Commands`

- check service status
```
sudo systemctl status httpd
```

```
journalctl -xe
```
- check system logs
- `x` flag shows the explanations

```
sestatus
getenforce
```
- get status of SE Linux if enforcing or permissive

```
setenforce 0
systemctl restart httpd
systemctl status httpd
```
- disable linux and check if service is running after that

Stop it first and set SE Linux back to enforcing
```
sudo systemctl stop httpd
sudo systemctl status httpd
setenforce 1
sestatus
getenforce
```

Start it back and check the log files
- check log files for error and commands that might fix these
```
systemctl start httpd
systemctl status httpd

journalctl -u httpd
sudo grep httpd /var/log/audit/audit.log | less
sudo ausearch -c 'httpd' --raw
```

Fix SE Linux Permissions
```
sudo ausearch -c 'httpd' --raw | audit2allow -M my-httpd-pol

semodule -i my-httpd-pol
```

Check if `HTTPD` works
```
curl localhost:85/test.html
```

Check for logs again
```
sudo grep 'httpd\|test.html' /var/log/messages | less
```

Check SE Linux permissions
```
ls -laZ /web
```
- use the `Z` flag for this

```
sudo semanage fcontext -a -t httpd_sys_content_t "/web(/.*)?"
sudo restorecon -Rv /web
```