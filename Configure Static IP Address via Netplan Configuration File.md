First create a `01-network-manager-all.yaml` backup file `01-network-manager-all.yaml.backup`
```
sudo cp /etc/netplan/01-network-manager-all.yaml /etc/netplan/01-network-manager-all_backup.yaml
```
Edit the file.
```
vi /etc/netplan/01-network-manager-all.yaml
```
-- If you want to `configure multiple IP addresses`, add all IP addresses one by one as shown below.
```
network:
  version: 2
  renderer: networkd
  ethernets:
    ens18:
      dhcp4: no
      addresses:
        - 192.168.1.22/24
        - 192.168.1.23/24
        - 192.168.1.24/24
      routes:
        - to: default
          via: 192.168.1.101
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
```

Before applying any changes, always validate the configuration using the command:
```
sudo netplan try
```
---Apply the Configuration.
```
sudo netplan apply
```
-- Restart the Network Service (Optional):
```
sudo systemctl restart systemd-networkd
```