# evm - Erlang Version Manager

This is a simple script which aims to simplify the management of different Erlang versions installed on your system. **evm** will allow you to install multiple versions of erlang on your system and easily switch between them. **evm** is like **rvm** (<https://rvm.io>) but with fewer features.

## Installation

Download **evm**, unzip it, and in the top level directory simply execute:

    $ ./install

Then add the following line to your .bashrc file:

    source $HOME/.evm/scripts/evm

That will create some directories inside your $HOME/.evm dir:

- **erlang_tars** : the place where all the erlang tarballs downloaded by evm will be cached.
- **erlang_versions** : where the erlang enviroment will be installed.
- **scripts** : the location of the evm script itself.
- **evm_config** : contains a single file pointing to the _default_ erlang version.

After installing **evm**, you can check if everything is okay by executing:

    $ evm help

If you see a list of **evm** commands, then your installation succeeded.

## Usage

- **list** (`$ evm list`)
    This will display the names of all the available erlang versions from <http://www.erlang.org/download.html>

- **install** (`$ evm install <version> [-y] [--with-docs] [<other configure options>]`)
    This will download the erlang tarball identified by **\<version\>** ( if not already downloaded ), then evm will install erlang by simply executing ./configure, make, make install, passing some default values.  The downloaded erlang tarball will be stored in a cache directory.

    You also will be given a chance to download any erlang dependencies you need--install will halt after the ./configure command has finished.

    Note: **evm** *will not* download the erlang dependencies for you.
    
    If you are sure you have all dependencies installed, and you don't want to be asked about continuing with the installation, specify the option **-y** *after* the erlang version. This will make the script continue with the installation without asking you anything.
    
   If you want to install documentation along with erlang, specify the option **--with-docs**. You can later access documentation using `$ erl -man mnesia` for example.
- **installed** (`$ evm installed`)
    This will show all the erlang versions installed by evm on your system.

- **download** (`$ evm download <version>`)
    This will download the specified erlang version from <http://www.erlang.org/download.html>, then evm will store it in a cache directory for future installation.

- **remove** (`$ evm remove <version>`)
    This will remove the specified erlang version from the cache; and if the specified erlang version is installed, this will uninstall it.

- **uninstall** (`$ evm uninstall <version>`)
    This will uninstall the specified erlang version--however the erlang tarball will remain in the cache directory, and evm won't need to download the erlang tarball again to install it.

- **cache** (`$ evm cache`)
    This will list all erlang versions that have been downloaded by evm (not necessarily installed).

- **system** (`$ evm system`)
    If you have an erlang version installed outside evm, this will change the PATH to use that version.

- **use** (`$ evm use <version>`)
    This will change the PATH to use the specified erlang version--if it was installed.

- **version** (`$ evm version`)
    This will show the current version of evm running on your machine.

- **help** (`$ evm help`)
    This will show something similar to below (thanks to neowulf33):

```
    EVM Home:
        ${EVM_HOME}
    Default Version:
        ${default_version:-"None"}
    Versions Ready To Use:
        ${available_versions:-"None"}

    Usage:
        * evm list
            Lists the available erlang versions which can be downloaded and 
	    installed.
        * evm cache
            Lists the available erlang versions which are in the evm space 
	    but not necessarily installed.
        * evm download [version]
            Downloads the erlang version.
        * evm install [version] [-y] [--with-docs] [erlang config options]
	    Downloads and installs the specified erlang version.
	    Use -y when you want to skip confirmation after the ./configure step.
	    -y will perform the installation even if dependencies are not met.
	    Do not use -y if you want to stop and check the dependencies.  
	    You can use --with-docs to build and install documentation for
	    erlang modules. You can also pass extra options to erlang install.
	    Extra options will be passed as is to the ./configure step, e.g.:
		   evm install OTP_18.3 --with-ssl=/usr/local/ssl
        * evm installed
            Lists erlang versions which are built and are ready to be used.
        * evm use [version]
            Switches to the specified erlang version.
        * evm default [version]
            Makes the specified erlang version the default.
        * evm remove [version]
            Removes the specified erlang version completely from the evm space.
        * evm uninstall [version]
            Uninstalls the specified erlang version but keeps it within the 
	    evm space.
        * evm system
            Alters the PATH in the current shell to use the non-evm erlang.
        * evm version
            Prints the current version of evm.
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
