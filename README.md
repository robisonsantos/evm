# EVM - Erlang Version Manager

This is a simple script which aims to make it easy to manage different Erlang versions installed on your system.
## Installation

Simply execute:

    $ ./install

Then add the following line to your .bashrc file:

    source $HOME/.evm/scripts/evm

That will create some directories inside your $HOME/.evm dir:

- **erlang_tars** : the place where all erlang tarballs downloaded by evm will be cached.
- **erlang_versions** : where the erlang enviroment will be installed.
- **scripts** : the location of the evm script itself.
- **evm_config** : contains a single file pointing to the current _default_ erlang version in use.

After installing evm, you can check if everything is okay by executing:

    $ evm help

If you see a list of evm commands, then your installation succeded.

## Usage

**evm** is like **rvm** (<https://rvm.io>), but with fewer features.
evm will allow you to install multiple versions of erlang on your system and easily switch between them.


- **list** (`$ evm list`)
    This will fetch all the available erlang versions from <http://www.erlang.org/download.html> and display their names.
- **install** (`$ evm install <version> [-y] [--with-docs] [<other configure options>]`)
    This will download the erlang tarball identified by **\<version\>** ( if not yet downloaded ), and then evm will simply execute ./configure, make, make install, passing some default values.

    You also will be given a chance to download any erlang dependencies you need--install will halt after the ./configure command has finished.

    Note: EVM *will not* download the erlang dependencies for you.
    
    If you are sure you have all dependencies installed, and you don't want to be asked about continuing with the installation, use the option **-y** *after* the erlang version. This will make the script continue with the installation without asking you anything.

   If you want to install documentation along with erlang, pass in the option **--with-docs**. You can later access documentation using `$ erl -man mnesia` for example.
- **installed** (`$ evm installed`)
    This will show all the installed erlang versions on your system.

- **download** (`$ evm download <version>`)
    If the specified erlang version is available, this will download it from <http://www.erlang.org/download.html>, then evm will store it for future installation.

- **remove** (`$ evm remove <version>`)
    If the specified erlang version has been cached on your system, this will remove it.  If it has been installed, this will also uninstall it.

- **uninstall** (`$ evm uninstall <version>`)
    If the specified erlang version has been installed on your system, this will uninstall it.

- **cache** (`$ evm cache`)
    This will list all erlang versions currently cached on your system.

- **system** (`$ evm system`)
    If you have erlang installed outside evm, this will change the path to use that version instead.

- **use** (`$ evm use <version>`)
    This will change the path of your current shell to use the specified erlang version--if it's already installed.

- **version** (`$ evm version`)
    This will show the current version of evm running on your machine.

- **help** (`$ evm help`)
    This will show something similar to below (thanks to neowulf33):

```
    EVM Home: 
        /home/robison/.evm
    Default Version:
        R15B01
    Versions Ready To Use: 
        R16B
        R15B01

    Usage:
        * evm list
            Lists available erlang versions which can be downloaded and installed on the system.
        * evm cache
            Lists available erlang versions which are in the evm space and not necessarily installed.
        * evm download [version]
            Downloads the erlang version.
        * evm install [version] [-y] [--with-docs] [erlang config options]
            Downloads and installs the specified erlang version.
            Use -y with you want to skip confirmation after configuration step.
            If -y is passed as argument the installation will happen even if dependencies are
            not met. Do not use -y if you want to check dependencies are ok.
            If you pass --with-docs, evm will compile and install erlang documentation, so you can use "erl -man <module>"               to check module documentation in the console. 
            You can also pass any extra parameters to erlang install. Any extra parameter will be passed
            as is to './configure' step. E.g evm install OTP_18.3 --with-ssl=/usr/local/ssl
        * evm installed
            Lists erlang versions which are built and are ready to be used.
        * evm use [version]
            Begins to use the specified erlang version.
        * evm default [version]
            Makes the specified erlang version as the default erlang version.
        * evm remove [version]
            Removes the erlang version completely from the evm space.
        * evm uninstall [version]
            Uninstalls erlang but keeps the erlang version within the evm.
        * evm system
            Alters the PATH within the shell to use the non-evm erlang.
        * evm version
            Print the currrent version of evm
```


## Dependencies

This script is dependent on:

- *wget*

## Erlang dependencies

On Debian based systems, this is the list of dependencies you probably need:

   sudo apt-get install openssl libssl-dev fop xsltproc unixodbc-dev libxml2-utils libwxbase2.8 libwxgtk2.8-dev libqt4-opengl-dev

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Added some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

