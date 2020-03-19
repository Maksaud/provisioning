# Using Vagrant provisioning
In this repository is a VM, vagrant file which uses a Provision file to update and install files.

```ruby
Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/bionic64"
  config.vm.network "private_network", ip: "192.168.10.100"
  config.hostsupdater.aliases = ["development.local"]
  config.vm.synced_folder 'app', '/app_destination'
  config.vm.provision 'shell', path: 'environment/provision.sh'
end


```
The code to provision to install some packages such as nginx and node js

```bash

#!/usr/bin/env bash


sudo apt-get update -y
sudo apt-get upgrade -y
sudo apt-get install git
sudo apt-get install nginx -y
sudo apt-get install nodejs -y
sudo apt install build-essential
curl -L https://npmjs.org/install.sh | sudo sh
sudo npm install pm2@latest -g
```
## running a virtual machine
- vagrant up command is to initialise and start the VM
- vagrant ssh to enter into the virtual machine
- inside vm use exit to exit the Virtual machine
- vagrant destroy to delete the virtual machine
- vagrant reload - To restart the virtual machine so that changes are made.
