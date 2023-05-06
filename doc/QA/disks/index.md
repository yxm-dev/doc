---
title: "doc/QA/disks"
---

* Q: how to create a `.iso` file from a directory of files using builtin commands?
* A: use the `mkisofs` command.

* Q: how to create a bootable USB flash drive from a `.iso` using only builtin commands?
* A: 
    1. insert the USB drive;
    2. use `lsblk` command to verify where the drive is mounted;
    3. unmount it with `umount` command;
    4. use `dd` command to create the flash USB.

* Q: how to create a bootable USB flash drive from a `.iso` *easily* from terminal?
* A: use the [bootiso](https://github.com/jsamr/bootiso) tool.

* Q: how to format a pendrive using only builtin commands?
* A: 
    1. use `lsblk` command to list mounted devices;
    2. identify the mount point (say `/dev/sdx`);
    3. umount the USB disk with `sudo umount /dev/sdx`;
    4. identify its file system type: `vfat` for less than `4G`, and `ext4` else.
    5. format the disk  with the `mkfs` command: `mkfs -t type /dev/sdx`.

* Q: after formatting a pendrive it is not being recognized.
* A: you have to establish a mountpoint, say `/usr/media` or `/mnt`:
```
    sudo mkdir -p [mountpoint]
    sudo mount -t auto /dev/sdx [mountpoint]
```

* Q: for some catastrophic reason I cannot login in the console, even with the root. How can I made a backup?
* A: 
    1. using another computer download the .iso of Arch Linux
    2. create a bootable pendrive (see above)
    3. plug the pendrive in the broken computer and boot in it
    4. insert another disk where you want to save your files
    5. after the boot, use `lsblk` to identify where
        * the broken disk is located, say `/dev/sdX`
        * the additional disk is located, say `/dev/sdY`
    6. use `mount /dev/sdX /mnt` to mount the broken disk in the system in the pendrive
    7. in `/mnt` you will see your files. Copy them to the additional disk with `cp -r /mnt/file /dev/sdY`
