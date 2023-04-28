---
title: "dev/doc/linux/settings"
---

The following is a list of softwares and settings I have been used in the last years. The marked items are those that we are currently using.

In very few words, I use:
* `Arch`, as my linux distribution
* `i3`, as my windows manager
* `Xterm` as my terminal.
I try to do everything is possible inside `Xterm`. If something cannot be realized in a terminal I realize it in a browser. I use:
* `Firefox`, for diary stuff
* `Tor`, when privacy is needed.
My text editor is `vim`. I use `mutt` as my mail client.
       
operating system
-----------------

* Lubuntu
* [Arch](arch) (*)

windows system
----------------

* `X11` (*)

windows manager
-----------------

* Openbox
* `i3`: tiling windows manager

terminal emulator
--------------------

* Lxterminal
* Xterm (*)

* **Remark**: I use `Liberation Mono` font. In Arch it is in the package `ttf-liberation`. 

drivers
---------

* ALSA driver [sound] (*)
    * `amixer+alsamixer`: builtin CLI and TUI managers for ALSA. (*)
    * `pulseaudio`: daemon for multiplex sound stuff (*)
        * `pulseadio-alsa`: package to allow pulseaudio to control ALSA (*)
        * `pavucontrol`: GUI for pulseaudio
    
* INTEL driver [video] (*)
    * `xrandr`: a daemon for INTEL driver (*)
    * `lxrandr`: GUI for `xrandr`
     
* `networkmanager` [wireless] (*)
    * `nmcli+nmtui`: CLI and TUI interfaces for `networkmanager`. (*)
    * `wf-sh`, part of `ecl-sh`: simple interactive mode for `nmcli`. (*)
    
packages
-------------------

* `base`: basic packages for usage (*)
    * `bash`
    * `systemd`
    * `pacman`
    * `tar`
    * `unzip`
    * (...)
* `base-devel`: basic packages for installing from the source for development (*)
    * `automake`
    * `autoconfig`
    * `libtools`
    * `bison`
    * (...)
* `cmake`
* `wget`

tools
--------

* `bc`: command line calculator (*)
    * used in several shell scripts, as in `bkl.sh`
* `xsel`: command line X11 selection and clipboard manipulation tool (*)
    * used with `w3m` to copy to clipboard the url under cursor
* `scrot`: command line screen saver (*)
    * used in the `lock.sh` script
* `fzf`: terminal-based fuzzy finder tool. (*)
    * used in `pm.sh`
* `pandoc`: command line markup languages translator. (*)
    * used in `cvt.sh`
    * see below
* `imagemagick`: command line image manipulation and conversion. (*)
    * used in the `lock.sh` script
* `ffmpeg`: command line video manipulation and conversion (*)
    * used in `cvt.sh`
* `sox`: command line audio converter (*)
    * used in `cvt.sh` 
* `zathura`: simple pdf reader. (*)
    - `zathura-djvu`: add compatibility with `djvu` files (*)
    - `zathura-pdf-mu-pdf`: add some features and compatibility with `epub` files (*)
* `rsync`: command line to sync files locally and remotely
    * used in  `sync.sh`
* `rclone`: command line to sync files with/between clouds
    * used in `bkp.sh`
* `git`: version control system
* `github-cli`: command line client for Github
* `docker`: containerization application
    
compilers/interpreters
------------------------

* `Bash` (*)
    * is in `base` package
* `GNU Make`
    * require part of the packages in `base-devel`.
    * if missing something, run `automake --add-missing`
* [Texlive](Texlive):
    * with ... for:
        * ...
* [Python](Python)
    * `python-pip`: package manager for `python`
        - `khard`
* [Haskell](Haskell)
    * a lot of libraries
        - `pandoc` 
* [Ruby](Ruby)
    * `rubygems`, for:
        - `Jekyll`
* [Go](Go), for: 
    *  `spotify-tui`
* [Nodejs](Node)
    * `npm`: package manager for `Node.js`.
        - `dicio`: [link](npm install --global dicio)
        - `gramma`: [link](https://github.com/caderek/gramma)

text
------

* `Vim` (cli): text-based terminal-based extendable text editor (*).
    * `Vimwiki` (*)
        * `Vimwiki-cli` ([link](https://github.com/sstallion/vimwiki-cli))
        * `Vim-Calendar`
    * `Vimtex` (*)
        * `Vimtex-Colors` (*)
    * [fzf-bibtex](fzf-bibtex): bibtex manager based on `fzf`.  ([link](https://github.com/msprev/fzf-bibtex))
    * `Vim-Snippets`
    * usar vim+python: [link](https://realpython.com/vim-and-python-a-match-made-in-heaven/)
* `Nano`: used only to install Arch.

web
----

* Browsers
    * `W3M`: text-based terminal-based browser.
    * `Firefox`: open-source browser.
    * `Tor`: privacy-based browser.
        
* Email
    * `Mutt`: text-based email client (*) 
    * `Abook`: address manager compatible with Mutt [link](https://github.com/hhirsch/abook)  
    * `Khard`: address manager compatible with Mutt (*)

media
--------

* Spotifyd: daemon for Spotify
* Spotify-Tui: terminal-based user interface for Spotify

other
-------

* `translate-shell`: terminal-based interface for google translator ([link](https://github.com/soimort/translate-shell))
    * `trsl-sh`: simple interactive mode for `translate-shell`
* `dicio`: CLI for [dicio.com.br](https://www.dicio.com.br/), a Portuguese dictionary ([link](npm install --global dicio))
* `grammar`: ClI grammar checker based on [LanguageTool](https://languagetool.org/) ([link](https://github.com/caderek/gramma))

