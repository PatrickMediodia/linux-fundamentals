```
stat <directory/file>
```

```
getfacl <directory/file>
```

```
setfacl -Rm <u/g/o>:<user/group>:<perms/rwx> // changes the existing files
setfacl -Rm <default entry>:<u/g/o>:<user/group>:<perms/rwx> // default on file create
```

```
Sets the `gid` bit
```

**Set GID**
```
chmod g+s <directory/file>
```
- use +s to set the owner of the files created to be the same owner as the directory
- this sets the new files to be created to inherit the group of the directory

**Sticky Bit**
```
chmod o+t <directory/file>
```
- directory with the "sticky bit" set places restrictions on file deletion
- a file in a sticky directory may only be removed or renamed by a user if the user has write permission for the directory and the user is the owner of the file, the owner of the directory, or the superuser.
- sticky bit does not allow users to delete other's files

