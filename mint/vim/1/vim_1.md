---
title: "Vim: a highly stable terminal-based text editor" 
---

Every Linux user needs a text editor. It is the place where every development is made. There are hundreds of
options, from the most simple to the highly elaborated. This article is the first of a column to Ubuntu Mint,
dedicated to `Vim`: a highly customizable and highly stable text editor, which is terminal-based and has been
developed since 60s.

* VIM IMAGE HERE

Origins
------

In the early history of operating systems, we find `Unix`, developed by Bell Labs in the 1960s, which was
accompanied by a text editor called `Ed`, an abbreviation for editor. In the early 1970s, Ed was replaced by a
more modern version called Ex (short for extended). At that time, everything had a `CLI` (command line
interface) and, therefore, everything operated directly through command lines. It was not different with `Ex`.

With the advancement of technology, `TUI` (terminal-based user interface) applications started to be developed.
Although they are not `CLI`, `TUI` applications are also carried out within a terminal. By the late 1970s,
Unix replaced `Ex` and started using a `TUI` text editor called `Vi`: an abbreviation for "visual",
referencing the shift from command lines to a visual interface.

`Unix` operating systems were not open-source. However, they were highly sought after due to their
portability, which motivated many people to focus on the problem of building open-source versions of Unix
applications. For example, the `Linux` kernel emerged from the attempt to replicate the kernel of `Minix`, one
of the `Unix` versions, in an open-source format. The same happened with the text editor `Vi`.

Indeed, in 1991, Bram Moolenaar developed a software that aimed to be an open-source version of `Vi`. He named
it `Vim`, which originally stood for "`Vi` IMitation". However, `Vim` ended up being developed as a much more
sophisticated fork of `Vi` and packed with many tools, leading to a change in the meaning of the acronym `Vim`
to "`Vi` IMproved". Over the years, `Vim` has evolved with a focus on simplicity, modularity, and
customization.

Characteristics
------

Vim was developed in the `C` programming language, making it independent of the shell used in `Unix`. This
allowed for the release of `Vim` versions for different operating systems. A scripting language called `Vim
Sript` was developed to standardize and facilitate the creation of modules, referred as "plugins".

One of the remarkable features of `Vi` is the use of keybinds: it involves mapping keyboard patterns to
actions, making command execution simpler, faster, and more customizable. This characteristic has been
preserved and remains predominant in `Vim`.

`gVim`
--------

In the 1980s, the first `GUI` applications started to emerge on `Macintosh` and `Windows 1.0` computers. While
maintaining its minimalist style, a `GUI` version of Vim was released in 1998, called `gVim`.

Installing
-----------

Installing `Vim` and `gVim` in `Ubuntu` is very simple from the `apt` package manager:

```bash
    sudo apt-get install vim
    sudo apt-get install vim-gtk3
```

Conclusion
--------

Thus, `Vim`:

* is a text editor created in 1991 as a fork of a text editor that has existed since the 1970s, making it
  extremely stable and extensively tested; 
* is an open-source software and cross-platform, with versions available for Linux, Windows, macOS, and more;
* was initially developed in a terminal-based user interface (`TUI`) format, but also has a minimalist
  graphical user interface (`GUI`) version called `gVim`;
* is highly extensible, allowing for the use of plugins that add additional functionalities and features;
* is fully customizable, allowing users to configure and personalize various aspects of the editor to suit
  their preferences and workflow;
* is very easy to install in `Ubuntu`.
