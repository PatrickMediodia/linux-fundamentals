- system and service manager
- backwards compatible with sysfile? init scripts
	- replaced upstart in RHEL based systems
- advanced features
	- allows parallel execution of services
- conductor for various parts of a linux system

Systemd DIrectories
- `/usr/lib/systemd/system`
	- rpm packages place their systemd unit files here during installation
- `/run/systemd/system`
	- unit files that are created at run time
	- overrides the `/usr/lib/systemd/system`
- `/etc/systemd/system`
	- unit files created by invoking systemctl enable
	- overrides `/run/systemd/system`

![[Pasted image 20240920232355.png]]
- Unit
	- descries the service
	- specifies the ordering dependencies and conflicting units
- Service
	- sequence of custom scripts to be ran during unit
		- execution
		- on stop
		- on reload
	- specifies the things to be 
- Install
	- list units that depend on the service

```
# usual commands
systemctl status <service>
systemctl start <service>
systemctl stop <service>
systemctl restart <service>

# show the systemd service file
systemctl cat <service>

# enable or disable based on boot needs
systemctl enable <service> --now // enables it so that it runs in subsequent boots
systemctl disable <service> --noq

# targets
sudo systemctl get-default
sudo systemctl set-default multi-user
sudo systemctl list-units
```

References:
https://documentation.suse.com/smart/systems-management/html/systemd-management/index.html