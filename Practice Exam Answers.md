1. create a user margarita with id number 3456

```
useradd margarita -m -u 3456
```

2. change the password of margarita to "mbautista"

```
passwd margarita
```

3. add a group named "interns"

```
groupadd interns
```
  
4. add "interns" as user margarita's secondary group

```
usermod margarita -aG interns
```


5. create the directory and /phitopolis/teams/interns

```
mkdir -p /phitopolis/teams/interns
```

6. make the group interns the owner of /phitopolis/teams/interns

```
chown :group /phitopolis/teams/interns
```

7. change the permissions of /phitopolis/teams/interns into 775

```
chmod 775 /phitopolis/teams/interns
```

8. as user "root", give the user "margarita" read write execute access to /phitopolis/teams/devops and its contents

```
setfacl -m user:margarita:rwx /phitopolis/teams/devops
```

  9. view the content of /phitopolis/teams/devops/manual.txt

```
cat /phitopolis/teams/devops/manual.txt
```

10. find the difference of /phitopolis/teams/devops/manual.txt and /phitopolis/teams/devops/new_manual.txt
  
```
diff /phitopolis/teams/devops/manual.txt /phitopolis/teams/devops/new_manual.txt
```

11. edit the manual.txt to be the same as new_manual.txt. after this, rename the manual.txt into "manual.txt.bak"

```
cat /phitopolis/teams/devops/new_manual.txt > /phitopolis/teams/devops/manual.txt
mv /phitopolis/teams/devops/manual.txt /phitopolis/teams/devops/manual.txt.bak
```

12. go to the directory /phitopolis/teams/devops/systems/files

```
cd /phitopolis/teams/devops/systems/files
```

  13. archive everything inside the directory /phitopolis/teams/devops/systems/files into "all_files.tar". Compress it into "all_files.tar.gz"

```
touch /phitopolis/teams/devops/systems/files{1..100}
cd /phitopolis/teams/devops/systems/files
tar -cvf all_files.tar .   // creates all_files.tar
tar -czvf all_files.tar.gz all_files.tar
```

14. copy "all_files.tar.gz" into /phitopolis/teams/interns. and then extract all the contents inside

```
cp /phitopolis/teams/devops/systems/files/all_files_tar.gz /phitopolis/teams/interns
cd /phitopolis/teams/interns
tar -xzvf all_files.tar.gz
tar -xvf all_files.tar

```

15. delete "all_files.tar.gz" file

```
rm all_files.tar.gz
```

16. show all the contents of /usr/share/ . Go to dict.

```
ls /usr/share
cd /usr/share/dict
```

17. get all words that has "ing" in it in/usr/share/dict/words
  
```
cat words | grep ing

```

18. change hostname to mbautista.local

```
hostname mbautista.local // change temporarily
hostnamectl set-hostname mbautista.local //change permanently
```

19. as user margarita, go to your home directory. make a file named myfile.txt . In this file append the following information.
	- Present working directory
	- the current user
	- the current date
	- If you have no idea about this try checking the manuals

```
cd
touch myfile.txt
pwd >> myfile.txt
whoami >> myfile.txt
date >> myfile.txt
```

20. check current disk space usage and report to gio

```
df -H
```

21. create an alias for the clear command. The alias name should be "wow"

```
alias wow=clear // temporary

vim bash.rc
alias wow=clear // append to the end of the file
source .bashrc // permanent solution
```

22. ssh to the IP 192.168.1.119 as the user "drazen", password is "romero". make it that the system wont ask for the password.

```
ssh-keygen
ssh-copy-id -i ~/.ssh/id_rsa.pub drazen@192.168.1.119 // this appends it to the authorize_keys file on drazen server
```
`