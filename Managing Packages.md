- uses `yum` or `dnf`

Repositories
- how to configure a repository
```
sudo vi /etc/yum.respos.d/epel.repo


[epel]
name=<name for repository>
baseurl=<baseURL>
enable=<0/1>
gpgcheck=<0/1>

sudo yum clean all
sudo yum repolist --all

sudo yum list --available <package>
sudo yum list --installed <package>

sudo yum check-update | less
sudo yum update
```

