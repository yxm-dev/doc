---
title: "doc/QA/go"
---

**Q**: How can I import a `file.go` file to a project `main.go` whose main directory is `main/`? <br>
**A**: there are at least two approaches:

1. work with module and package:
    * in `main/` init a module with `go mod init`;
    * create a directory `main/files` and put `file.go` there (in `Go` this defines a "package");
    * in `file.go` certify that it begins with `package files`;
    * in `main.go` import `file.go` as follows:
```go
        package main
        import "dir/files"
```
2. work in the `GOPATH`:
    * put your directory `main/` in `$GOPATH/src/`;
    * if you want, create a dir `$GOPATH/src/main/files` and put `file.go` there. Otherwise, you can put it
      together with `main.go`;
    * in `main.go` import `file.go` as follows:
```go
        package main
        // if files.go is in main/files/:
        import "main/files/file"
        // if files.go  is in main/:
        import "./file"
```
        
