-------------
    Ruby       
-------------

In the following we describe how to install the latest version of Ruby from the source and from the package manager in Arch Linux.

Remove Previous Version
-------------------------
* verify the installed version with `ruby -v`. 
    * If there is no output, jump to Ruby install instructions
    * else
        * if the installation was made from package manager, then: `pacman -Runs ruby` 
        * else if the installation was from the source and the installed version is `z.z.z`, then 
``` 
    cd ruby-z.z.z
    sudo make uninstall ruby
```  

Install Ruby
---------------


0. remove the already installed version `z.z.z`
    * for installation from the source: 
   
    * for installation from package manager:
        * Debian-based OS: `sudo apt-get remove ruby`
        * Arch Linux:

1. download the latest version `x.x.x` in the official site ([link](https://www.ruby-lang.org/en/downloads/))
2. extract the files
```
    tar -xfz ruby-x.x.x.tar.gz 
```
3. enter in the directory
```
    cd ruby-x.x.x
```
4. build and install
```
    ./configure
    make
    sudo make install
```
5. verify the installed version: ``ruby -v``

Alternatively, Ruby can be installed from snap: `sudo snap install ruby-x.x.x.`

Install RubyGems
------------------

1. clone the official GitHub repository
```
   git clone https://github.com/rubygems/rubygems
```
2. enter in the directory: `cd rubygems`
3. install with `ruby setup.rb`
4. update to latest version `y.y.y`: 
```
    sudo gem update --system y.y.y
```

Troubleshooting
-----------------

* If got message `/lib64/libcrypt.so.1: version 'XCRYPT_2.0' not found`, add this to the `~/.profile` file:
```
    export LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/usr/lib64:/usr/lib/x86_64-linux-gnu/libcrypt.so.1:/lib64"
```
