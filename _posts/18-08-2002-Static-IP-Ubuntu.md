## cek dulu gatewaynya
```
route
```
## gas static ip
```
sudo su
vim /etc/netplan/00-installer-config.yaml
```
## edit
```
# This is the network config written by 'subiquity'
network:
  ethernets:
    enp0s3:
      dhcp4: false
      addresses: [192.168.56.100/24]
      gateway4: 192.168.56.0
      nameservers:
        addresses: [8.8.8.8,8.8.4.4]
  version: 2
```
## terapkan
```
netplan apply
```
## cek
```
ifconfig
```
