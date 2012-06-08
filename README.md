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

**TODO:** Improve the help message. It's currently just printing a useless message

If that executes fine, then you'll should have a list of actions you can execute:

- *list* (`$ evm list`)
    This will fetch all the available erlang tarball versions from <http://lynx.isc.org/> presenting you a list of them.

- *install* (`$ evm install <version>`)
    This will download the erlang tarball identified by *version* ( if not yet downloaded ) and then it will simply execute **./configure - make - make install** passing some default values.

    It will also give you a chance to download any erlang dependency you need, by stopping the process after the **./configure** command has finished.

    **Obs:**: EVM *will not* downalod the erlang dependencies for you.

- *installed* (`$ evm installed`)
- *download* (`$ evm download`)
- *remove* (`$ evm remove`)
- *uninstall* (`$ evm uninstall`)
- *cache* (`$ evm cache`)
- *system* (`$ evm system`)
- *use* (`$ evm use`)
- *help* (`$ evm help`)

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
