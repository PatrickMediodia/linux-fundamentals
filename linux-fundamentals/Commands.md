- `whoami`
- `pwd`
- `ls`

Volumes
- `df -h | grep /dev/sda`

RPMs
- install - `sudo rpm -i htop-2.2.0-3.el7.x86_64.rpm`
- uninstall - `sudo rpm -e htop`

Debian
- version - `cat /etc/issue`
- install - `sudo dkpg -i htop_2.0.2-1_amd64.deb`
- uninstall - `sudo dpkg --remove htop`

Installing from Source
- Uncompress files - `tar xzf htop-2.2.0.tar.gz`
- Run the configure script
	- `cd htop-2.2.0`
	- `./configure`
- Compile the source code - `make`
- Install the binary - `sudo make install`
- Uninstall the binary - `sudo make uninstall`
```
( cd '/usr/local/share/applications' && rm -f htop.desktop )
( cd '/usr/local/bin' && rm -f htop )
( cd '/usr/local/share/man/man1' && rm -f htop.1 )
( cd '/usr/local/share/pixmaps' && rm -f htop.png )```

