---
title: "dev/doc/linux/QA/devices"
---

* Q: after installing `X11` desktop environment my keyboard layout is not being recognized.
* A:
    1. use `loadkeys` to load your keyboard layout;
    2. pass the command `setxkbmap`;
    3. if everything is working, add the `setxkbmap` setting to the `.xinitr` file or in the configuration file of your windows manager (e.g., `i3/config` in the case of `i3` windows manager).
    
* Q: after installing `X11` desktop environment my touchpad or other device is not working properly.
* A:
    1. install `libinput` package;
    2. use of `xinput` to configure the device - see [here](https://wiki.archlinux.org/title/libinput).
    3. alternatively, edit/create the file `/etc/X11/xorg.conf.d/40-libinput.conf` and add to it the settings you want;
    4. the available settings are in the [documentation](https://wayland.freedesktop.org/libinput/doc/). See also the [Arch documentation](https://man.archlinux.org/man/libinput.4).
    * If even after configuration with `libinput` the device is not working properly, you should try to install `Synaptics` drivers and then follows one of the two approaches described above - see [here](https://wiki.archlinux.org/title/Touchpad_Synaptics). 
    * For example, in the case of touchpad in Arch Linux, try the old package `xf86-input-synaptics`.  

