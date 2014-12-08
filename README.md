# EVM - Erlang Version Manager

This is a simple script which aims to make easy the management of different Erlang versions in your system.

## Installation

Simply execute:

    $ ./install

And then add the following line to your .bashrc file:

    source $HOME/.evm/scripts/evm

This will create some directories inside your $HOME/.evm dir:

- **erlang_tars** : the place where all erlang tarballs downloaded by evm will be cached.
- **erlang_versions** : where the erlang enviroment will be installed.
- **scripts** : the location of evm script itself.
- **evm_config** : contains a single file pointing the current _default_ erlang version in use.

## Usage

**EVM** is based on **RVM** (<https://rvm.io>), but of course without that so many features.
It will help you to have as many erlang versions you like in your system, switching between them as easy as possible.

After the installation, you can check if everything is ok by executing:

    $ evm help

If that executes fine, then you'll should have a list of actions you can execute:

- *list* (`$ evm list`)
    This will fetch all the available erlang tarball versions from <http://www.erlang.org/download.html> presenting you a list of them.

- *install* (`$ evm install <version>` [-y])
    This will download the erlang tarball identified by *version* ( if not yet downloaded ) and then it will simply execute **./configure - make - make install** passing some default values.

    It will also give you a chance to download any erlang dependency you need, by stopping the process after the **./configure** command has finished.

    **Obs:**: EVM *will not* download the erlang dependencies for you.
    
    If you are sure you have all dependencies installed and don't want to be asked about continuing with the installation, use the option -y AFTER the erlang_version. This will make the script continue with installation without asking anything to you.

- *installed* (`$ evm installed`)
    This will show all the installed erlang versions on your system.

- *download* (`$ evm download <version>`)
    If the version informed is available, this command will download it from <http://www.erlang.org/download.html> and then it will store it for future installation.

- *remove* (`$ evm remove <version>`)
    If the version informed has been chached on your system, this option will remove it. Note that if the informed version is installed, the command will also uninstalled it.

- *uninstall* (`$ evm uninstall <version>`)
    If the version informed has been installed on your system, this option will simply uninstall it.

- *cache* (`$ evm cache`)
    This will list of erlang versions currently cached on your system.

- *system* (`$ evm system`)
    If you have erlang installed outside EVM, then this command will change the path to include that version instead.

- *use* (`$ evm use <version>`)
    This will change the path of your current shell to use the specified erlang version, if it's already installed.

- *version* (`$ evm version`)
    This will show the current version of this script running on your machine.

- *help* (`$ evm help`)
    This will show something similar as bellow (thanks to neowulf33):

## EVM help

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
        * evm install [version]
            Downloads and installs the specified erlang version.
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
            Alters the PATH within the shell to use the non-evm erlang


## Dependencies

This script is dependent on :

- *lynx* (<http://lynx.isc.org/>)
- *wget*

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Added some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
