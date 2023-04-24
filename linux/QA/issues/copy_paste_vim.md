---
title: Copy and Paste to Clipboard in Vim
author: Yuri X. Martins
---

* **Remark.** The following is for the X11 windows environment.

Compatibility
=================

The first step is to ensure that your `Vim` installation is compatible with clipboard.

1. In a terminal type
```
    vim --version | grep clipboard
```
If `+clipboard` and `+xterm_clipboard` are reported (notice the `+` sign), your vim installation already supports clipboard and you can go to the configuration step.

2. if the options follow a `-` sign, them there is no compatibility. To fix this:
    * in a Debian-based distro, install `vim-gtk` package from the [source](https://pkgs.org/download/vim-gtk3) or from your distribution package manager:
    ```
        sudo apt install vim-gtk
    ``` 
    * in Arch Linux and related distro, the package manager dos not provide to `vim` native support to clipboard. On the other hand, it does to `gvim`. In this case, the easiest option is to remove `vim`, install `gvim` and pass to use the `vim` internal to `gvim` as your text editor:
    ```
        sudo pacman -Runs vim
        sudo pacman -S gvim
    ```
3. Repeat step (1.) to confirm that your `vim` installation is now compatibility with clipboard. 

Configuration
================

In your `vimrc` file (located in `~/.vim`) add the following:
```
    "copy and past from clipboard
    set clipboard+=unnamed
    set go+=a
```

Keybind
==========

As a final (and optional step), you can replace Vim's standard keybinds to copy (`y`), cut (`c`) and paste (`p`) with your favorite ones.

* **Remark.** In Vim, `"` means the selection of a register. In X11, `+` means "to clipboard". Thus, `"+` means to select the clipboard register, so that you should map your favorite keybinds to `"+y`, `"+c` and `"+p`.

For example, to cut, copy and paste with `ctrl+c`, `ctrl+x` and `ctrl+v`, add the following to your `vimrc` file:
```
    vnoremap <c-x> "+ci
    vnoremap <c-c> "+yi
    inoremap <c-v> <esc> "+pi
```

References
==============

* https://stackoverflow.com/questions/11489428/how-to-make-vim-paste-from-and-copy-to-systems-clipboard 
