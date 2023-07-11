 ---
 title: `makepkg` as a root in Arch
 author: yxm
 date:
 ---
 
There are two basic groups that exist in a linux distribution: the `root` and the `nobody`. In Arch-based
distributions binaries are managed through the `makepkg` command. Due security reasons, users in the `root`
group cannot directly use `makepkg`. The immediate approach would be to create a non root user and run the
command from it. In the following we describe another approach: to momentarily use an user in the already
existing `nobody` group.

Preparing a directory 
======================

1. create a directory `/home/dir` outside of the exclusive domain of `root` group:
```
    mkdir /home/dir
```
2. set the `nobody` group as the owner of `dir`, ensuring that `nobody` users have permission to write in `dir`:
```
    chgrp nobody /home/dir
    chmod g+ws /home/dir
```
3. pass the same permissions for subdirectories and file in `/home/dir`:
```
    setfacl -m u::rwx,g::rwx /home/dir
    setfacl -d --set u::rwx,g::rwx,o::- /home/dir
```

Using `makepkg`
=================

4. clone binary files directly in `/home/dir` or move the directory, say `bindir` containing them
5. execute `makepkg` as a `nobobody` user:
```
    cd /home/dir/bindir
    sudo -u nobody makepkg
```
6. if you got an error "*You do not have write permission for the directory $BUILDDIR*", then force the
   permission of `/home/dir/bindir/` and execute `makepkg` again as a nobody user:  
```
    chmod g+ws /home/dir/bindir
    sudo -u nobody makepkg
```
7. delete `/home/dir/`, if you want.

Automation
==============

1. add the following function to  `.bashrc` file, or paste it in a `.sh` file and move it to `/usr/bin/`

```bash
    function mkpkg(){
        bindir=$(basename $PWD)
        mkdir /home/dir
        cp -r $PWD /home/dir/
        chgrp nobody /home/dir/$bindir
        chmod g+ws /home/dir/bindir
        cd /home/dir/$bindir
        sudo -u nobody makepkg $@
        cd $OLDPWD 
        rm -r /home/dir
}

```
2.  execute `mkpkg` inside the `bindir`.
