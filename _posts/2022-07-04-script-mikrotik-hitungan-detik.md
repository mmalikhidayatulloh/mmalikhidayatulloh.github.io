#Requirements

ether1 as WAN

ether2,3,4,5 as LAN

#Script
```
/ip dhcp-client add interface=ether1 disable=no
/interface bridge add name=bridge-WAN
/interface bridge add name=bridge-LAN
/interface bridge port add bridge=bridge-WAN interface=ether1
/interface bridge port add bridge=bridge-LAN interface=ether2
/interface bridge port add bridge=bridge-LAN interface=ether3
/interface bridge port add bridge=bridge-LAN interface=ether4
/interface bridge port add bridge=bridge-LAN interface=ether5
/ip address add address=192.168.1.1/24 interface=bridge-LAN
/ip firewall nat add action=masquerade chain=srcnat out-interface=bridge-WAN
/ip dhcp-server setup
bridge-LAN





/ip dhcp-server enable dhcp1

/ip dns set servers=8.8.8.8 allow-remote-requests=yes

```

#Source

https://lms.onnocenter.or.id/wiki/index.php/Mikrotik:_Router_Sederhana
