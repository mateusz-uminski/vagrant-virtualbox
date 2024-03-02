# vagrant-virtualbox

[![verify](https://github.com/mateusz-uminski/vagrant-virtualbox/actions/workflows/verify.yaml/badge.svg?branch=main)](https://github.com/mateusz-uminski/vagrant-virtualbox/actions/workflows/verify.yaml)

This vagrant code provisions environments that I use in my test environment to learn new things and verify crazy ideas. Besides the README.md further documentation can be found in commits, code comments and nested README files.
<br><br>
Feel free to explore and copy everything you want.
Enjoy!

# Requirements
1. Vagrant version ~> 2.2.19
2. Virtualbox

## Usage

```sh
CONFIG_FILE=vmachines/default.yaml vagrant up --provision
```
