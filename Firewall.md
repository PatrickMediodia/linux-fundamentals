<<<<<<< HEAD
---

---
Install `firewalld`
```
sudo yum install -y firewalld
sudo systemctl status firewalld
sudo systemctl enable --now firewalld
```

Editing `firewalld` conf
```
sudo grep -i '^AllowZoneD' /etc/firewalld/firewalld.conf
```

Change `firewalld` status
- `sed -i` is in place replacement and not on disk
```
sudo sed -i -e 's/AllowZoneDrifting=yes/AllowZoneDrifting=no/' /etc/firewalld/firewalld.conf
```

Reload the systemd service after editing
```
sudo systemctl reload firewalld
```

```
sudo firewall-cmd --zone=public --add-service=http --permament // this will apply after system boot
sudo firewall-cmd --zone=public --add-service=http // this will set it right now

sudo firewall-cmd --zone=public --add-service=https --permament
sudo firewall-cmd --zone=public --add-service=https
=======
```
nmap -A <ip> | less
```
- used scan and check all the ports

```
firewall-cmd --help | less
```
- important flags
	- reload - pickup the changes
	- list-all - list all of the services

```
firewall-comd --add-service=<service name>
```

```
firewall-cmd --list-services
```
- list only all of the services

```
firewall-cmd --add-port=85/tcp --permanent
```
- add all of the ports to the config

**Lab**
```
curl localhost
```

```
yum install -y httpd
```

```
systemctl status httpd
```

```
systemctl enable --now httpd
>>>>>>> 546512f039b39268a224c55276f220dfe2a0272e
```