**Lab**

Find out the groups of the users
```
groups mortimer clarice caruso
```

Get the FACL rules of the current directory
```
getfacl /opt/ProjectA/
```

Set the FACL of the Project A directory
```
setfacl -m g:managers:rwx /opt/ProjectA/
```

Know if there are FACLs on the directory
- it has if there is a + in the end
```
ls -ld /opt/ProjectA
```

Giving others access to your directory
```
setfacl u:<user>:rwx /opt/ProjectA/
```

Backup FACL settings
```
getfacl -R /opt/ProjectA/ > ~/ProjectA.acl.bu
```

Removing access for a user using ACLs
```
setfacl -m user:caruso:--- /opt/ProjectA/
```

Getting ACLs from backup
```
setfacl --restore=/home/mortimer/ProjectA.acl.bu
```
