---
title: "doc/QA/environment"
---

**Q**: I created a keybind in `i3` that executes a bash script defined in `~/.bashrc`, but it does not work.
Why?<br>
**A**: `i3` does not load `~./bashrc`. Thus, just call the script from the absolute path. See [here](https://stackoverflow.com/questions/50968451/bash-script-works-in-terminal-emulator-but-not-as-i3-keybind).

**Q**: I do not use a display manager. After login in the console I have to type `startx` to see my graphical
  environment. How to automate this?<br>
**A**: 

1. copy the file `/etc/skel/.bash_profile` to `$HOME/.profile`
2. in the booting process, this file is read after login and before starting the graphical environment
3. in it add the following:
    
```bash
# startx after login
    if [[ -z "$DISPLAY" ]] && [[ $(tty) = /dev/tty1 ]]; then
        source startx
        logout
    fi
``` 
