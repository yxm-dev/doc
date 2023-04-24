---
title: "dev/doc/linux/QA/bash"
---

* Q: how to execute an external application `foo` in terminal such that the shell section becomes free to use and clean?
* A: use `foo & disown` to execute the application in background and `clear` to clean the terminal. Thus, the issue is fixed with `foo & disown | clear.`

