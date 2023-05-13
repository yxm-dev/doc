---
title: "doc/QA/error"
---

**Q**: I'm facing with a message saying that `/dev/null` was not found.<br>
**A**: Just create a file with same properties:
```bash
    sudo rm /dev/null
    sudo mknod -m 0666 /dev/null c 1 3   
``` 

