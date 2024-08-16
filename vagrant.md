# Vagrant------


### how to up vagrant vm.
```
vagrant up
```
### vagrant machine ssh
``` 
vagrant ssh
```
### check vagrant status.
``` 
vagrant status 
```

## Port Forwarding
Networking allows access to the Virtual machine from outside(like from the host system).
Vagrant by default forwards port 22 from the guest machine (VM) to an open in the machine.

Step 1 - Open vagrantfile and add this line
```
config.vm.network "forwarded_port", guest:80, host:8080
```
Step 2 - Restart VM with updated Vagrantfile 
```
vagrant reload --provision
```
Step 3 - open the browser 
```
localhost:8080 
```

## If port 8080 is busy--
step 5 - Add auto-correction option ```auto_correct:true``` in Vagrantfile 
by default, Vagrant will choose auto-correction port between port 2200 and port 2250 range.


## Private Networks

### DHCP--
Configure a bridge network with DHCP
```
config.vm.network "public_network", bridge: "your_network_interface", type: "dhcp"
```

### Static ip--
```
config.vm.network "public_network", bridge: "en0p1:", ip: "192.168.1.20"
```










