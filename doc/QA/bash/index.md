---
title: "doc/QA/bash"
---

**Q**: how to execute an external application `foo` in terminal such that the shell section becomes free to
use and clean?<br>
**A**: use `foo & disown` to execute the application in background and `clear` to clean the terminal. Thus,
the issue is fixed with `foo & disown | clear.`


**Q**: how to collect the base names of subdirectories of a directory `dir` in an array `subdirs`?<br>
**A**: 

1. in a general case, mix `find` with `printf`:
```bash
    $(find dir -type d -printf "%f\n")
```
2. in the presence of the `basename` tool, you can also use it: 
```bash
    $(find dir -type d | xargs basename)
```
4. another alternative is:
```bash
    find . -type f -exec basename {} \;
```
*  of course, same argument holds for different settings of `find`, including fixing `depth` or finding for files.
    

**Q**: how to check if an element `x` belongs to an array `A`?<br>
**A**: use the test `[[ "${A[@]}" =~ "$x" ]]`

* notice that in this case the order inside the brackets is the opposite in comparison with the other tests. 
 
