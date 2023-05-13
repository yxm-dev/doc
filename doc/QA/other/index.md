---
title: "doc/QA/other"
---

**Q**: `rsync` is repeating the synchronization ordering even after switching source and target files. Why?<br>
**A**: `rsync` stores temporary files. Remove them using the following or do a reboot:

```bash
    find -type f -iname ".*.*.??????" -delete
```

**Q**: I'm trying to install `texlive` from my distro binary but I'm facing errors. What can I do?<br>
**A**: install from the source, as detailed [here](https://tug.org/texlive/quickinstall.html). Basically:

1. install `perl`
2. download the source from [here](https://mirror.ctan.org/systems/texlive/tlnet/install-tl-unx.tar.gz)
3. extract, enter in the directory and do a `perl ./install-tl` (this takes some time)
4. and add the corresponding directory `/usr/local/texlive/...` to the PATH. 
