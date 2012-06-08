evm
===

Erlang Version Manager
----------------------

This is supposed to be a simple script to help managemenet of multi version of Erlang in the same machine.

So far the help message is not ready :), but if you want to use it right now, simply execute the install script - which will create some directories in your home (execute the last line of the installation report):

~/.evm/erlang_tars
~/.evm/erlang_versions
~/.evm/evm_config
~/.evm/scripts

To use this script, you first need to install lynx (<http://lynx.isc.org/>).

After that execute `$ evm list` to list all available erlang version on <http://www.erlang.org/>.

To install erlang R14B04, for instance, execute `$ evm install R14B04` 

To use and specific version, already installed in your system, execute `$ evm use R14B04`

To mark one version as default in the system, execute `$ evm default R14B04`

TODO: Improve the help

This script was based on RVM (Ruby Version Manager)
