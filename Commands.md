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

Going to your home directory
- `cd`
- `cd ~`
- `cd $HOME`

`cd -` - go to the last directory you were in

Paths
- Absolute
	- `/path/from/root`
	- specify the path starting from the root
- Relative
	- `path/relative/to/current/directory`
	- path that is relative to the working directory to where you are right now

Directories and Listing Files
- `ls -lat var/log` - oldest file
- `ls -lS var/log` - sort by largest file
- `ls -l sos_commands/networking/netstat_-W-neopa` - when file was last modified
- `ls -lu sos_commands/networking/netstat_-W-neopa` - when the file was last accessed

Directory Commands
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