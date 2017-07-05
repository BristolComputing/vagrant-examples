# vagrant-examples
Vagrant is a useful tool to quickly create pre-defined Virtual Machines (VMs)
for easier code development. E.g. a user can run Windows/OS X/Ubuntu but
compile & run the software on CentOS 6/7.

This repository gives vagrant examples and explains customization options.

## Example overview:
  - cernvm: examples based on the CernVM image (Scientific Linux 6)

## Prerequisites
1. Install [Virtualbox](https://www.virtualbox.org/wiki/Downloads)
2. Install [Vagrant](https://www.vagrantup.com/downloads.html)
3. (Recommended on Windows) Install [Git for Windows](https://git-scm.com/downloads)

## General Usage
Let's say you have an existing project folder that contains the code with the name
`myproject`. The first step is to pick one of the example Vagrant files and save it
under `myproject/Vagrantfile`.

By default most examples will map the `myproject` folder on the host machine
to `/vagrant` on the VM. This means you can use any editor available on the host
machine and compile & run the code in the VM.

Full documentation for vagrant commands can be found on the [official Vagrant site](https://www.vagrantup.com/docs/index.html).

## On Unix
To start the VM:

```bash
cd <path to myproject>
vagrant up
vagrant ssh
```

To stop the VM
```bash
vagrant halt
```

## On Windows
Navigate to the project folder, right-click on it and select `Git Bash Here`.
This will open a unix-like shell that you can use for Vagrant and git commands.

```bash
vagrant up
```

You can now either use `vagrant ssh` to get into the machine or use the GUI (if enabled).


For specific instructions please see the relevant example folders.


## Customization
### Shared folders
Folders are shared between the host machine and the VM by `config.vm.synced_folder`
instructions in the Vagrantfile (see [documentation](https://www.vagrantup.com/docs/synced-folders/basic_usage.html)).

### Provisioning instructions
In case you want to execute a certain set of action when `vagrant up` is called
for the first time (or `vagrant provision`) you can use the `config.vm.provision`
instructions. E.g. to copy a file from the host machine:
```ruby
config.vm.provision "file", source: "~/.gitconfig", destination: "/home/vagrant/.gitconfig"
```
or to execute shell commands
```ruby
config.vm.provision "shell", inline: <<-SHELL
        sudo mkdir /software
        sudo chown vagrant /software
  SHELL
```

### Resource usage
Resource usage is controlled by the instructions
```ruby
# RAM usage
vb.memory = "2048"
# CPU usage
vb.cpus = 2
```
