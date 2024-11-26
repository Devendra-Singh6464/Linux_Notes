### Vagrant installation https://developer.hashicorp.com/vagrant/install
```shell 
wget -O- https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update && sudo apt install vagrant
```
After install vagrant check vagrant --version.
```
vagrant --version
```
Create a directory.
```
mkdir -p myvm/myvag
```
change directory--
```
cd myvag 
```
Initialize the project.
```
vagrant init ubuntu/focal64
```
```
vi Vagrantfile
```
edit this line and " write name of your box"
```
config.vm.box = "ubuntu/focal64"
```
like this. starting the file.
```
# Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  config.vm.box = "ubuntu/focal64"
```

```
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/focal64"
  config.vm.box_version = "20240821.0.1"
end
```
Install a box vagrant box add.
```
vagrant box add ubuntu/focal64
```
 If your want install another box so https://portal.cloud.hashicorp.com/vagrant/discover visit this link and select. and install 
```
vagrant up
```
vagrant machine ssh
``` 
vagrant ssh
```
check vagrant status.
``` 
vagrant status 
```

## Port Forwarding
Networking allows access to the Virtual machine from outside(like from the host system).
Vagrant by default forwards port 22 from the guest machine (VM) to an open in the machine.

Step 1 - Open vagrantfile and add this line.
```
config.vm.network "forwarded_port", guest:80, host:8080
```
Step 2 - Restart VM if your any changes with Vagrantfile. 
```
vagrant reload --provision
```
Step 3 - open the browser.
```
localhost:8080 
```
--- If port 8080 is busy:
step 4 - Add auto-correction option ```auto_correct:true``` in Vagrantfile 
by default, Vagrant will choose auto-correction port between port 2200 and port 2250 range.

## Assigned the IP-
--- DHCP
Configure a bridge network with DHCP.
```
config.vm.network "public_network", bridge: "your_network_interface", type: "dhcp"
```
--- Static IP.
```
config.vm.network "public_network", bridge: "en0p1:", ip: "192.168.1.20"
```
Vagrant default password.
```
vagrant
```
Create vagrant box.
```
vagrant package
```

## Share Vagrant-box
```

```