


Dependences
==============
    * `fzf`  ([link](https://github.com/junegunn/fzf))
    * `fzv.vim` ([link](https://github.com/junegunn/fzf.vim))
    * `bibtool` ([link](https://ctan.org/pkg/bibtool))
    * `go`

Installation
===============

* For `fzf`:
```
    git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf
    ~/.fzf/install
```
* For `fzf.vim`: as usual.
* For `bibtool`: use package manager.
* For `fzf-bibtex`:
```
    go install github.com/msprev/fzf-bibtex/cmd/bibtex-ls@latest
    go install github.com/msprev/fzf-bibtex/cmd/bibtex-markdown@latest
    go install github.com/msprev/fzf-bibtex/cmd/bibtex-cite@latest
    sudo mv ~/Go/bin/ /usr/bin
```

