---
title: "doc/QA/vim"
---

* Q: my colorscheme is not being recognized by `Vim` but it does if I force a `:set colorcheme` inside some document.
* A: copy your `colorscheme.vim` file (or create a symlink) to `/usr/share/vim/vimX/colors/`, where  `X` denotes the version of your Vim. 

* Q: default `Vim` copy and paste shortcuts are working only internally to `Vim`, i.e., I cannot copy inside `Vim` and paste outside `Vim`.
* A: 
    1. if you are in a Debian-based system, install the package `vim-gtk`
    2. in Arch-based systems, remove `Vim` and install `gvim`
    * see [here](copy_paste_vim) for detailed explanation.

plugins
---------

* Q: After installing the [indentLine](https://github.com/Yggdroot/indentLine/issues/303) plugin links in [Vimwiki](https://github.com/vimwiki/vimwiki) files are not working properly.
* A: base on commented from [here](https://github.com/Yggdroot/indentLine/issues/303), just add the following to your `vimrc` file:
```
    let g:indentLine_fileTypeExclude = ['vimwiki', 'markdown', 'md']
    let g:indentLine_bufTypeExclude = ['help', 'terminal', 'vimwiki', 'markdown', 'md']
```
