---
title: "dev/doc/linux/QA/other"
---

* Q: `rsync` is repeating the synchronization ordering even after switching source and target files. Why?
* A: `rsync` stores temporary files.
    1. You can delete it using
```
    find -type f -iname ".*.*.??????" -delete
```
    2. Alternatively, since temporary files are deleted in the shutdown processes, a reboot also fixes the issue.

