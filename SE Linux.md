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
ausearch -c '<search string>' --raw | less 
grep '<search string>' /var/log/messages | less
ls -laZ <directory/file> // shows the selinux content for a file or directory
```

```
semanage fcontent -a -t <idk> <lol>
restorecon -Rv <dir>
```