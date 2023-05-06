---
title: configuring backlight brightness and creating hotkeys to manage it
---

There are three steps:

1. configure the backlight driver;
2. install a software to manage backlight;
3. create keybindings to map keys to the software functionalities.

* **Remark**. In the following we will use the software [Light](https://github.com/haikarainen/light), which can be used with any backlight driver and in any windows environment. A common alternative is [xbacklight](https://github.com/tcatm/xbacklight), but it is compatible only with the Intel driver and with X11 windows environment. Similar steps applies, however, to [xbacklight](https://github.com/tcatm/xbacklight) or any other software. 

# Configure

The first thing to do is to find the file in `/sys/` where brightness is configured:

```
    sudo find /sys/ -type f -iname '*brightness*'

```

This allows us to identify what is the backlight driver. Indeed, resulting file is of the form  `/.../driver_blabla/brightness`, where `driver` is the name of your driver. For example, a possibility is `driver_blabla=intel_backlight`, which means that the driver is Intel.

If the located file is contained in the directory `/sys/class/backlight/`, then it is done. Otherwise, create that directory and in it create a file called `driver_blabla`. Then, link this file with the starting file `.../driver_blabla/brightness` that controls brightness:

```
    sudo ln -s /.../driver_blabla/brightness /sys/class/driver_blabla

```

* **Remark.** If the software to be used is `xbacklight` (which means that the drive is Intel and the windows environment is X11), then there is one more configuration step. Verify if the file `/etc/X11/xorg.conf` already exists and contains 
```
    Section "Device"
        Identifier  "Intel Graphics" 
        Driver          "Intel"
        Option          "Backlight"  "intel_backlight"
    EndSection
```
If it does, then its done. Otherwise, create that file with this content.

# Installing 

Install a backlight command line software as [Light](https://github.com/haikarainen/light) or [xbacklight](https://github.com/tcatm/xbacklight) following its manual instructions.

For example, ....

```
    apt get install xbacklight

```

After installation, look at the manual again, now to get the commands controlling brightness. If the software is named `software`, probably it would work as

```
    software [option] [value]
```

Furthermore, certainly there are two options, say `-i` `-d`, such that for every value `x` the command `software -i x` (resp. `software -d x`) increases (resp. decreases) brightness by `x`. 

For example, the basic usage of `light` is 

```
    light [option] [value]

```
and the options `-A` and `-U` are responsible to increase and decrease brightness, respectively. Similarly, for `backlight` we have

```
    xbacklight [option] [value]

```

and the options are now `-inc` and `-dec`.

# Keybinding

Finally, having identified the commands that increase/decrease brightness, we just need to bind them to some keys. 


# References
1. arch linux documentation: [https://wiki.archlinux.org/title/backlight](link)
2. ask ubuntu question: [https://askubuntu.com/questions/715306/xbacklight-no-outputs-have-backlight-property-no-sys-class-backlight-folder/1060843#1060843](link)
3. superuser question: [https://superuser.com/questions/1279727/xfce-change-brightness-steps-and-or-change-brightness-key-behavior](ink)

