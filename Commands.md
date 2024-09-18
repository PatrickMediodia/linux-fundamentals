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
( cd '/usr/local/share/pixmaps' && rm -f htop.png )
```

Determining the version of the host
- `cat /etc/*release`
- `cat /etc/*issue*`
- `lsb_release -a`
- `hostnamectl`

Directories
- `pwd` - print current directory
- `cd ~` - go to home directory

Logins
- `w` - check user logins
```
 00:36:37 up  1:14,  1 user,  load average: 0.51, 0.52, 0.37
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
cloud_us pts/0    136.158.78.243   00:35    0.00s  0.04s  0.00s w
```
- `last` - history of logins
```
cloud_us pts/0        136.158.78.243   Sun Aug 18 00:35   still logged in
reboot   system boot  4.4.0-1128-aws   Sat Aug 17 23:22   still running
```

Redirects
- `{command} > {redirect to}`
	- ex. `w > log.txt`
	- overwrites the contents of `log.txt` with the output of the `w` command
	- if `log.txt` does not exist, it creates the file
- `{command} >> {redirect to}`
	- ex. `last >> log.txt`
	- appends the output of the command to the redirect
	- creates the file if it does not exist

Modifying the `$PATH` variable
- `echo $PATH` - show the current path variable
```
/home/cloud_user/bin:/home/cloud_user/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
```
	- it will look for executables in the paths
	- separated by colon :
- `PATH=$PATH:$HOME/scripts` - append the home directory/scripts path to the path variable
	- this allows us to run scripts in the scripts folder without specifying the whole path
- `echo 'PATH="$PATH:$HOME/scripts"' >> .profile`
	- a more permanent approach
	- append the new `$HOME/scripts` directory to your path variable and add it to the bottom of your `.profile` file

**Quoting Lab**
- `This is 'just' a "test".`
```
variable1="This is 'just' a \"test\"."
```

- `This is a backslash "\" and this is a single quote '.`
```
variable2="This is a backslash \"\\\" and this is a single quote '."
```

- `3 double quotes """, and 3 single quotes \'\'\', and three backslashes \\\.`
```
variable3="3 double quotes \"\"\", and 3 single quotes \'\'\', and thr
ee backslashes \\\\\\\\\."
```

-  `This is what a newline character looks like \n, it will create a new line.`
```
variable4="This is what a newline character looks like \\\n, it will c
reate a new line"
```

- `cat value.txt`
```
This is 'just' a "test".
This is a backslash "\" and this is a single quote '.
3 double quotes """, and 3 single quotes \'\'\', and three backslashes \\\.
This is what a newline character looks like \n, it will create a new line
```

- Note: Use double backslash to escape a backslash

**Echo**
- `-e` - allows the interpretation of backslash escapes

**Man Pages**
- `/{search string}` - search through a man page
- `n` - go to the next occurrence of your search string
- `N` - go back to the previous occurrence of your search string
- `man -k {search string}` - searches your string in the description of commands that are available
	- useful for remembering commands
	- same as `apropos {search string}`

**Info Pages**
- provide more detailed information about a command rather than its man page
- uses a structure for linking pages together
- may be assembled into a larger collection
	- `U` - show the larger collection
	- `N` - go to the next page in the collection
	- `P` - go to the previous page in the collection
- `info {command}`
- if no info page is provided, it will pull data from the man page

**Word Count**
- How many lines?
	- `wc -l longfile.txt`
- How many characters wide?
	- `wc -L longfile.txt`
- How many characters?
	- `wc -m longfile.txt`

**Show all users in a system**
- `cat /etc/passwd`
- shows the master mapping of users, user ids, and home directories
	- `pat:x:1000:1000:Pat,,,:/home/pat:/bin/bash`
- home directory is where you will be placed once you login to a system

**Going to your home directory**
- `cd`
- `cd ~`
- `cd $HOME`

`cd -` - go to the last directory you were in

**Paths**
- Absolute
	- `/path/from/root`
	- specify the path starting from the root
- Relative
	- `path/relative/to/current/directory`
	- path that is relative to the working directory to where you are right now

**Directories and Listing Files**
- `ls -lat var/log` - oldest file
- `ls -lS var/log` - sort by largest file
- `ls -l sos_commands/networking/netstat_-W-neopa` - when file was last modified
- `ls -lu sos_commands/networking/netstat_-W-neopa` - when the file was last accessed

**Directory Commands**
- `mkdir <directory>` - create new directory
- `cp -r <from dir> <to dir>` - copy files of a directory to another
	- recursively copy
- `mv <from dir> <to dir>` - change the name or move it to another directory entirely
	- `mv testdir2 /tmp/`
	- `mv testdir3 testdir2`
- `rm -rf <directory>` - recursively delete files in a directory
	- `r` - recursively delete files in a directory
	- `f` - force, no need for confirmation
- `touch <filename>` - create a file
- `file <filename>` - shows the type of file
- `cat <filename>` - print out the contents of a file
- `mv -T <from dir> <to dir>` - overwrite a directory
	- directory to be overwritten must be empty

**Case Sensitivity**
- lowercase and uppercase have different ascii representations
- `cat/etc/fstab`
	- shows file system mounts
- `ext4` is a case sensitive file system

**Globbing**
- partial matching to work with groups of files and directories
- uses wildcard characters to create a pattern
![[Pasted image 20240820190205.png]]
- `?` - matches every single character
	- ex. `ls ?????` - every file that has 5 characters will be returned
	- ex. `ls ????1` - every file that has 5 characters with 4 being any and it ending with 1
	- ex. `ls ????[1-3]` - every file that has any 4 starting characters and ends with 1 to 3
- `*` - matches 0 to any additional number of characters
	- ex. `*4` - every file with any length that ends in a 4
	- ex. `ls *[[:digit:]]` - matches anything that ends with a digit

**Directories and Files**
- `cp -R ~/Practice/Test ~/Report/` - copy Test into Report directory
- `mv ~/Practice/sos_commands/filesys/mount-l ~/Report/mounts.txt` - move the mount-l file to a new file named `mounts.txt`

**Archiving**
- tar is only to put files together, it does not compress them
![[Pasted image 20240821185657.png]]
- `tar` - tape archive
- `tar cf <tar file name>.tar <files to include>`
	- `tar cd archive.tar test_file_*`
	- creates a tar file of the files that are included
- `tar tf <tar file name>.tar`
	- `tar tf archive.tar`
	- `tar tvf archive.tar` - verbose
	- lists the file or contents of a tar file
- `tar rf <tar file name>.tar <files to append>`
	- `tar rf archive.tar file?`
- `tar xf <tar file name>.tar <files to extract>`
	- `tar xf archive.tar file3`
	- extract specific files
	- if directory, use relative path of the tar file
- `tar xf <tar file name>.tar`
	- `tar xf archive.tar`
	- extract every file in a tar file
- `tar xf <tar file name> --wildcards <file with globbing>`
	- `tar xf archive.tar --wildcards 'test_file_?'`
	- extract all files that start with test_file_ and 1 character after
	- when you widthdraw files from the archive, you are not removing them from being inside the archive
- `tar --delete --file=<tar file name>.tar <file to delete>`
	- `tar --delete --file=archive.tar file3`
	- delete a file from a tar
	- not usually used
	- usually extract it, work with it, and then put it back together

**Disk**
- `df -h` - show disk space and human readable

**Archives and Compression**
![[Pasted image 20240821191911.png]]
- `tar czf <archive file name>.tar.gz <files to include>`
	- gzip is the default compression algorithm used by tar
	- optimized for text files
	- good enough for most use cases
- `tar cjf <archive file name>.tar.bz2 <files to include>`
	- bzip2 file
	- alternative compression algorithm
	- slower than gz2 due to higher compression
- `tar xzf <archive file name>.tar.gz <files to extract>`
- `zip -r <zip name>.zip <files to include>`
	- appox the same as gzip
	- all in one compression algorithm
- `bzip2 <files to zip> <path to new bzip file>`
	- `bzip2 -d <file to decompress>`
- `gzip <files to zip> <path to new gzip file>`

- use `z` for gzip
- use `j` for bzip

**Pipe**
- output from one command as the input to another command
- `|` - pipe symbol
- `grep` - searches any given input files, selecting lines that match one or more patterns
	- `grep [OPTIONS] [PATTERN] [FILE]`
	- Sample
		- `grep -E ^M <file>`
			- find lines in file that start with an uppercase M
			- `-E` means an expression search
		- `cat <file> | grep <expression>`
			- the output of the cat file will be piped into the grep as the input as a specific file was not specified
		- `cat <file> | grep <expression> | wc -l`
			- cat the contents of a file to view it
			- use grep and then a regex expression to filter it out
			- count the number of lines that has been filtered
		- `!<command/expression>`
			- `!wc` - will rerun the last command that starts with `wc`
		- `cat /etc/passwd | grep root`
			- only show the information for a specific user
		- `cat /etc/passwd | grep root | cut -d: -f6`
			- only get the home directory for the user root
			- `:` is the delimiter
			- `-f6` means the 6th item in the `array` of items based on the delimiter
			- kinda like the `split` array function in python

**I/O Redirection**
- either feed and input to a command from a file
- or send the output of a command to a file
- commands
	- `cat <file> | grep <expression> > <file>`
		- send the output of cat that has been filtered with grep into a file
		- rather than displaying to `stdout`, it is written to a file
		- creates the file if it does not exist
		- if the file exists, it overwrites the file
	- `cat <file> | grep <expression> >> <file>`
		- appends to the end of the file rather than overwrite it
	- `cat <file> | sort >> <file>`
		- sorts the output of the file
		- and appends to the file
	- `grep <expression> < <filename>`
		- grep the outputs of filename

**Regular Expressions**
- pattern matching, kinda like globbing
- more discrete and way more flexible
	- `grep -E`
		- extended grep
		- this is the same as `egrep` but that has been deprecated
	- `^<expression>` - starts with
	- `<expression>$` - ends with
	- `<expression1>|<expression2>` - either expression1 or expression 2
	- `expression1*expression2` - anything between expression1 or expression2 with a length of 0 or more
		- ex. `cat <file> | grep -E "Ap*le"` vs `cat <file> | grep -E "Ap+le"`
			- the first expression also captures `ale` because `*` is 0 or more
			- the second expression needs to have atleast one instance `p` since it uses `+`
	- `+` - kinda like `*` but is 1 or more
	- `?` - maybe
	- `<expression>[digit range / letter range]<expression>` 
		- finds anything in between that is in the digit and letter range
		- in this case it only accepts one instance of this range
	- `ls -la /usr/share | wc -l`
	- `cat /var/log/dpkg.log | grep unpacked | wc -l`
	
	- `cat /usr/share/dict/words | grep -E "^l...x$"`
	- `cat /usr/share/dict/words | grep -E "^y..$|^z..$" | wc -l >> value.txt`

**Where Data is Stored**
![[Pasted image 20240902172407.png]]
- everything in `/etc` dir is configuration related
- `/boot` 
	- before, linux had the boot stuff in another partition
	- nowadays it is included in the same partition
	- `uname -r`
		- show the current kernel being used
- `/etc/fstab`
	- maps which disk partition to mount automatically
	- `blkid` - see the UUID of the block devices
- `/etc/passwd`
	- shows the users and their information
	- `<user>:<password>:<user-id>:<group-id>:<gekko/long name>:<home/login dir>:<login shell>`
- `/etc/group`
	- list of groups
	- `<group name>:<password>:<group-id>:<members of group>`
- `/etc/hosts`
	- mapping of host names and IP addresses
	- `ip hostname`
- `/etc/resolve.conf`
	- specify the name servers that we will look up our IP addresses to
- `/etc/<APPLICATION>`
	- has the configuration files for applications
- `/sys`
	- `mount | grep sysfs`
	- sysfs is a file system that is volatile and lives in the ram
	- export of the kernel data structure and their attributes and the link between them
	- virtual file system
	- export information about the different kernel subsystems

**Processes**
- data used by processes
- `PID (process id)` - unique identifier of a process
	- every process that is running will have a process id, which user that is running it, etc.
	- priority
		- the higher the number, the lower the priority
		- A value of `1` will be prioritized over lets say `20`
- `Process Data:` - `/proc/<PID>`
	- shows information about processes
	- you have a process folder for each process that is currently running
	- `cat /proc/self/status`
		- information about running processes
		- every running process has a status file
- `ps aux`
	- show every process in the system using the BSD syntax
	- prints it to be human readable
	- `ps aux | grep <user> | wc -l`
		- show the number processes for a user
- `ps -eF`
	- this is the same as aux and is more modern
- can use `top`/`htop` to see processes more interactively
- `/sys/`
	- system information regarding devices/attached hardware
- `/dev`
	- character or block device
	- something that is moving characters back and forth
	- stuff that is reading or writing to data of some kind
	- this makes it so that linux is able to treat the drive itself as a file
	- `/dev/sda` - hard drive
	- `dev/sda1` - the partition itself
	- `/dev/mapper` - used in LVMs to map the virtual block devices

**System Messaging**
- viewing and accessing system messages
- kernel messages are sent to a kernel ring buffer (circular queue)
	- a special buffer that remain constant in size
	- new messages come in and push out the old messages
- `dmesg`
	- print out the kernel ring buffer
	- used for troubleshooting hardware issues

**Logging**
- common locations for system and application log data
- application, event, system, service, kernel logs
- `/var/log/messages`
	- general system logs and messages
	- everything goes into this
	- `/var/log/syslog` - for debian based systems
	- `<date> <timestamp> <user> <system> : <log message>` 
- `/var/log/auth.log`
	- authentication logs
	- `/var/log/secure` - for red-hat based systems
	- PAM - pluggable authentication modules
		- anything involving PAM is authentication
	- `<date> <timestamp> <user> <subsystem> <log>`
- `/var/log/boot.log` - system boot logs
- `/var/log/cron.log` - cron job logs
- `/var/log/kern.log` - kernel logs
- `/var/log/faillog` - authentication failure logs

**Processes Lab**
- How many processes are currently running?
	- `ps -eF | wc -l`
- What is the current system load?
	- `uptime`
	- `cat /proc/loadavg`
- How many processes are running as `cloud_user`?
	- `ps -eF | grep cloud_user | wc -l`
	- `ps -U cloud_user | wc -l` - better because it actually gets for that specific user
- What is the PID of the `xfce4-session` process?
	- `ps -ef | grep xfce4-session | grep -v grep`
	- `grep -v grep` removes the grep command from the output
- How many threads is the `xfce4-session` process using?
	- find out the PID of the `xfce4-session`
		- `ps aux | grep xfce4-session | grep -v grep`
	- view the status to see the threads
		- `cat /proc/<PID>/status | grep Threads`
- Create a shell script for this
```
#!/bin/bash

# if the first parameter is not empty
if [ -n $1 ]
then
    _pid=$(ps aux | grep -E "$1\$" | grep -v grep | grep -v threads.sh | awk '{print $2}')
    cat /proc/$_pid/status | grep Threads
fi
```

**Viewing Logging Files Lab**
- Attempt to `curl` the address on the local host
	- `curl -I localhost` - only curl for the headers
- Determine how many times 10.0.1.10 has accessed the website
	- `sudo cat /var/log/httpd/access_log | grep -E "^10.0.1.10" | wc -l`\
	- `/var/log/http/access_log` - has the logs of who has tried to access `httpd`
	- `grep -E "^10.0.1.10"` - regular expression and must start with the IP `10.0.1.10`
- While viewing the access log, attempt to reach the web server from your computer via `http://[PUBLIC IP]/index.html`
- Find the new entry in the log
	- `sudo tail -f /var/log/httpd/access_log`
		- `-f` is follow, meaning all new entries will be appended to the bottom
	- `sudo cat /var/log/httpd/access_log | tail -10`
- Attempt to reach the web server from your computer via `http://[PUBLIC IP]/server.html`

**CRON**
- a daemon that runs in the background, it can execute things on an interval
- `crontab -l` - list out crontabs
- `crontab -e` - edit crontabs
- `cat /etc/crontab`
	- shows the crontab of a user
	- `<minute> <hour> <day> <month> <day of the week>`

**Networks**
- `ip addr show`
	- shows the list of IP addresses
	- loopback is always `127.0.0.1`
	- ipv4 is composed of 8 octets
	- the CIDR notation specific the portion of the address that is for networks and hosts/IPs
	- IPv4 is still widely used due to NAT and subnetting strategies
- `ping`
	- sends and ICMP network request
		- `-c` - count

**DNS Client Configuration**
- hostname --> IP address
- `host <hostname>` - shows the Ip address of a hostname
- `dig <hostname>` - shows more data than the host command
	- `dig @<DNS server> <hostname>` - specify the DNS that we want to get from
- `/etc/resolv.conf`
	- used to determine which hosts to use for DNS queries
	- also shows the configured DNS host (name server)
- `/etc/hosts`
	- used for statically mapping IP addresses to hostnames
	- used for development usually

**Network Configuration**
- `ip route show` - shows the routing table
	- `default` is the route
	- if local, it is in the other network interfaces
	- the router is the `catch all` or `else` clause
- `ifconfig` - might be deprecated soon
	- view and change interface configuration
- `nmcli` - little more information about the interfaces on your device
- `netstat` - view active connections
	- `-tlnp` 
		- `-t` - tcp
		- `-u` - UDP
		- `-l` - listening
		- `-n` - numeric (only show IPs)
		- `-p` - process IDs
	- `cat /etc/services | grep <port #>`
		- to know the process number running on a specific port

`getfacl` - get file access control lists
`/usr/bin` - this is where binaries are put and is automatically in the path there for you can execute it from everywhere
`which <binary/exec file>` - locate executable file associated with the command through the path environment variable

`ls -i` - shows the i-node number, if hard linked, this is the same

`diff` - search about this

edit sudoers file
- `visudo` - use this when editing

wheel group is full access
if may `%` sa name ng sudoers file, this is the 

tar file stuff
- compress
- uncompress
- check files inside

set hostname - `hostnamectl set-hostname`

`df -h` - disk space
`du` - disk usage

`alias`

passwordless ssh
- `ssh-keygen`
- `ssh-copy-id -i <key> <user>@<ip>`
- authorized keys
- `~/.ssh/authorized_keys`

`/etc/ssh/sshd_config`
- change `PermitRootLogin` - to be able to ssh as root

`touch filename{1..<n>}`

`sudo -l` - shows the list of permissions that the user can use `sudo` for

`passwd` - change the password of a user
`chage`

`mkdir -p` - create parent directories if not yet there

default file/directory - umask = default perms\
- file - 666
- directory - 777
- edit in `/etc/login.defs`

`setfacl` - 

`find <dir> -type f | grep <expression> | xargs`

`cd -` - go to previous directory 

`which <bin>` - shows the path of the binary that is being targeted

`cmp` - to show if there is a difference
`diff <file1> <file2>` - shows the actual difference

`find <directory> -name <filename> -type f -perm`

`cat /etc/resov.conf` - show your DNS server

`ufw allow 80` - ufw is a firewall
- `ufw status` - show ufw stuff

`traceroute <ip>` - shows the hops it took to get to the destination

`netstat -tulpn | grep <expression>` - shows the network stuff on your machine

`free` - shows RAM data about your system

`df -H` - shows the free disk space on your computer

`pkill -f <process name>` - no need to specify or know the process id

Managing Files and Permissions Lab
- `sudo passwd -l <user>` - lock a users account
- `last` - shows the last login for all the user
	- if a user is still logged in and you want to log them out, kill the process of their shell
- `for i in nancy greg jeremy; do sudo useradd -m $i; done` - create users with home directories `-m`
- `for i in nancy greg jeremy; do sudo userdel $i; done` - delete users
- `sudo userdel <user>` - remove previous user
- `sudo chown -R <new_user>:<new_group> /home/<old_user>` - recursively chown the directory of the old user to be owned by the new user
- `sudo chmod g+rw /home/<old_user>` - allow the group to be able to read and traverse the folder of the chowned used
	- note, you need to have execute access to be able to open a directory

**Temporary Files and Directories Lab**
- Get the files and put it in `/tmp`
	- `cd /tmp`
	- `wget <link>`
- Unarchive the tar file
	- `tar -xf <filname>.tar`
- Recursive ls the directory and put the output in a file
	- `tmp_file=$(mktemp)`
	- `ls -laR <directory> >> tempfile`
- Move the `version.txt` file to `/var/log` for more permanent storage
	- `mv <directory>/<file> /var/log`

Add a new path to the path variable
````
echo 'PATH=$HOME/<path>:$PATH' >> .bashrc
source .bashrc
````

Create new symlinks
```
ln -s /usr/lib/rpm/rpmdb_load /home/cloud_user/bin/rpm_load
ln -s /usr/lib/rpm/rpmdb_verify /home/cloud_user/bin/rpm_verify
ln -s /usr/lib/rpm/rpmdb_dump /home/cloud_user/bin/rpm_dump
```

SSH Into Another Server Without SSH Key
```
ssh-keygen
ssh-copy-id -i <key> <user>@<ip>
```

Execute a Command without opening their interactive shell
```
ssh <user>@<ip> <command>
```

SCP - Secure Copy
```
scp <user>@<ip>:<path to file or dir> <local path> // copy from remote to local
scp <local path> <user>@<ip>:<path to file or dir> // copy from local to remote
```

SFTP
```
sftp <user>@<ip>
mget <file path>
```

Man and Info Pages
```
// what you should probably check first, is shorter than others
<service> --help
<service> -?

// more comprehensive
man <service>
info <service>

// very barebones
whatis <service>
apropos <service> // also shows the specifics per page

// located in /usr/share/doc
```

Tree
```
tree <path> // you might want to use root permissions to be able to view all of the files
```

Aggregate service log files
```
sudo grep <service> <path> > stdout.log 2> stderr.log
// separate files for stdout and stderr

sudo grep <service> <path> >> stdouterr.log 2>&1
// one file for both stdout and error
// redirect stderr to where stdout is currently going
// &1 resuses the file descriptor

you can also send the the stdout and stderr to /dev/null to silence them

journalctl -u <service> --no-pager >> <path to file>
// send journalctl logs to path to file
```

```
egrep -v // reverse of what you specified, kinda like blacklisting
```