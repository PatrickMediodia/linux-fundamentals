![[Pasted image 20240918154004.png]]

```
ln -s <path to link> <link name>

ls -i // show soft links and link count
```

umask - view the umask
```
- user permissions - umask = final permissions
- echo 'umask 0027' >> ~/.bashrc
```

- soft links can point to files or folders that does not exist
- hard links needs to point to files or filders that DO exist
- 