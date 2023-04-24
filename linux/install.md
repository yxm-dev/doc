
Review the process of preparing the software to be used by the user.

* typically, "remove" and "uninstall" are considered synonymous. 

# pre-builded softwares

## from app repositories
* apt (Ubuntu)
* [npm](https://docs.npmjs.com/about-npm) (Node.js)

## from other resources
* .deb files: use `dpkg -c`, where `c=i` to install and `c=r` to remove.
* .snap files (be sure to have `Snapd` installed): `snap install` to install and `snap remove` to uninstall. 
* .flatpack files (be sure to have `Flatpack` installed): ...
* .AppImage files: no need of installation. Just make the file executable with `chmod +x` and execute it.

# from the source

* GNU Make
* Cargo
* Go
* Rust
* ...
