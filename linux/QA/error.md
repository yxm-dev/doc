---
title: "dev/doc/linux/QA/error"
---

* Q: I'm facing with a message saying that `/dev/null` was not found.
* A: Just recreate the file:
    ```
        sudo rm /dev/null
        sudo mknod -m 0666 /dev/null c 1 3   
    ``` 

