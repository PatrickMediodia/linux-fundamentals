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
```