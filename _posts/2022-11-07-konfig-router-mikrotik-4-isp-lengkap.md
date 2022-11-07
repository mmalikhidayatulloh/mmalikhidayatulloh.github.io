#RB450Gx4

```
/ip dhcp-client
add disabled=no interface=ether1
add disabled=no interface=ether2
add disabled=no interface=ether3
add disabled=no interface=ether4
/interface bridge
add name=bridge-lan
add name=bridge-cctv
/interface vlan
add interface=ether5 name=vlan100 vlan-id=100
add interface=ether5 name=vlan110 vlan-id=110
add interface=ether5 name=vlan200 vlan-id=200
add interface=ether5 name=vlan210 vlan-id=210
add interface=ether5 name=vlan300 vlan-id=300
add interface=ether5 name=vlan400 vlan-id=400
add interface=ether5 name=vlan500 vlan-id=500
add interface=ether5 name=vlan600 vlan-id=600
/interface bridge port
add bridge=bridge-lan interface=ether5
add bridge=bridge-cctv interface=vlan300
add bridge=bridge-cctv interface=vlan110
add bridge=bridge-cctv interface=vlan210
/interface list
add name=WAN
add name=LAN
/interface list member
add interface=ether1 list=WAN
add interface=ether2 list=WAN
add interface=ether3 list=WAN
add interface=ether4 list=WAN
add interface=bridge-lan list=LAN
add interface=bridge-cctv list=LAN
add interface=vlan200 list=LAN
add interface=vlan300 list=LAN
add interface=vlan400 list=LAN
add interface=vlan500 list=LAN
add interface=vlan600 list=LAN
/ip address
add address=17.17.1.1/24 interface=bridge17 network=17.17.1.0
add address=27.27.27.1/24 interface=vlan400 network=27.27.27.0
add address=37.37.37.1/24 interface=vlan500 network=37.37.37.0
add address=47.47.47.1/24 interface=vlan100 network=47.47.47.0
add address=57.57.57.1/24 interface=vlan200 network=57.57.57.0
add address=7.7.7.1/24 interface=vlan600 network=7.7.7.0
/ip pool
add name=dhcp_pool0 ranges=17.17.1.2-17.17.1.254
add name=dhcp_pool1 ranges=47.47.47.2-47.47.47.254
add name=dhcp_pool2 ranges=57.57.57.2-57.57.57.254
add name=dhcp_pool3 ranges=27.27.27.2-27.27.27.254
add name=dhcp_pool4 ranges=37.37.37.2-37.37.37.254
add name=dhcp_pool5 ranges=7.7.7.2-7.7.7.254
/ip dhcp-server
add address-pool=dhcp_pool0 disabled=no interface=bridge17 name=dhcp1
add address-pool=dhcp_pool1 disabled=no interface=vlan100 name=dhcp2
add address-pool=dhcp_pool2 disabled=no interface=vlan200 name=dhcp3
add address-pool=dhcp_pool3 disabled=no interface=vlan400 name=dhcp4
add address-pool=dhcp_pool4 disabled=no interface=vlan500 name=dhcp5
add address-pool=dhcp_pool5 disabled=no interface=vlan600 name=dhcp6
/ip dhcp-server network
add address=7.7.7.0/24 gateway=7.7.7.1
add address=17.17.1.0/24 gateway=17.17.1.1
add address=27.27.27.0/24 gateway=27.27.27.1
add address=37.37.37.0/24 gateway=37.37.37.1
add address=47.47.47.0/24 gateway=47.47.47.1
add address=57.57.57.0/24 gateway=57.57.57.1
/ip firewall mangle
add action=accept chain=prerouting dst-address=10.137.0.0/17 in-interface=ether1
add action=accept chain=prerouting dst-address=10.147.0.0/17 in-interface=ether2
add action=accept chain=prerouting dst-address=10.157.0.0/17 in-interface=ether3
add action=accept chain=prerouting dst-address=10.167.0.0/17 in-interface=ether4
add action=mark-connection chain=prerouting connection-mark=no-mark \
    in-interface=ether1 new-connection-mark=koneksi-1
add action=mark-connection chain=prerouting connection-mark=no-mark \
    in-interface=ether2 new-connection-mark=koneksi-2
add action=mark-connection chain=prerouting connection-mark=no-mark \
    in-interface=ether3 new-connection-mark=koneksi-3
add action=mark-connection chain=prerouting connection-mark=no-mark \
    in-interface=ether4 new-connection-mark=koneksi-4
add action=mark-connection chain=prerouting connection-mark=no-mark \
    in-interface-list=LAN new-connection-mark=koneksi-1 passthrough=yes \
    per-connection-classifier=both-addresses-and-ports:4/0
add action=mark-connection chain=prerouting connection-mark=no-mark \
    in-interface-list=LAN new-connection-mark=koneksi-2 passthrough=yes \
    per-connection-classifier=both-addresses-and-ports:4/1
add action=mark-connection chain=prerouting connection-mark=no-mark \
    in-interface-list=LAN new-connection-mark=koneksi-3 passthrough=yes \
    per-connection-classifier=both-addresses-and-ports:4/2
add action=mark-connection chain=prerouting connection-mark=no-mark \
    in-interface-list=LAN new-connection-mark=koneksi-4 passthrough=yes \
    per-connection-classifier=both-addresses-and-ports:4/3
add action=mark-routing chain=prerouting connection-mark=koneksi-1 \
    new-routing-mark=mangle-1
add action=mark-routing chain=prerouting connection-mark=koneksi-2 \
    new-routing-mark=mangle-2
add action=mark-routing chain=prerouting connection-mark=koneksi-3 \
    new-routing-mark=mangle-3
add action=mark-routing chain=prerouting connection-mark=koneksi-4 \
    new-routing-mark=mangle-4
add action=mark-routing chain=output connection-mark=koneksi-1 \
    new-routing-mark=mangle-1
add action=mark-routing chain=output connection-mark=koneksi-2 \
    new-routing-mark=mangle-2
add action=mark-routing chain=output connection-mark=koneksi-3 \
    new-routing-mark=mangle-3
add action=mark-routing chain=output connection-mark=koneksi-4 \
    new-routing-mark=mangle-4
/ip route
add check-gateway=ping distance=1 gateway=10.137.0.1 routing-mark=mangle-1
add check-gateway=ping distance=1 gateway=10.147.0.1 routing-mark=mangle-2
add check-gateway=ping distance=1 gateway=10.157.0.1 routing-mark=mangle-3
add check-gateway=ping distance=1 gateway=10.167.0.1 routing-mark=mangle-4
add check-gateway=ping distance=1 gateway=10.137.0.1
add check-gateway=ping distance=2 gateway=10.147.0.1
add check-gateway=ping distance=3 gateway=10.157.0.1
add check-gateway=ping distance=4 gateway=10.167.0.1
/ip firewall nat
add action=masquerade chain=srcnat out-interface-list=WAN
/system identity
set name=RB450Gx4
/tool romon
set enabled=yes
```

SW0

```
/interface bridge
add name=bridge1 vlan-filtering=no
/interface bridge port
add bridge=bridge1 interface=ether1
add bridge=bridge1 hw=no interface=ether2
add bridge=bridge1 hw=no interface=ether3
/interface bridge vlan
add bridge=bridge1 tagged=ether1,ether2 vlan-ids=100
add bridge=bridge1 tagged=ether1,ether2 vlan-ids=110
add bridge=bridge1 tagged=ether1,ether2 vlan-ids=200
add bridge=bridge1 tagged=ether1,ether2 vlan-ids=210
add bridge=bridge1 tagged=ether1,ether2 vlan-ids=300
add bridge=bridge1 tagged=ether1,ether3 vlan-ids=400
add bridge=bridge1 tagged=ether1,ether3 vlan-ids=500
add bridge=bridge1 tagged=ether1,ether3 vlan-ids=600
/interface bridge
set numbers=0 vlan-filtering=yes
/system identity
set name=sw0
/tool romon
set enabled=yes

SW1

/interface bridge
add name=bridge1 vlan-filtering=no
/interface bridge port
add bridge=bridge1 interface=ether1
add bridge=bridge1 interface=ether2
add bridge=bridge1 interface=ether3
add bridge=bridge1 hw=no interface=ether4 pvid=300
/interface bridge vlan
add bridge=bridge1 tagged=ether1,ether2 vlan-ids=100
add bridge=bridge1 tagged=ether1,ether2 vlan-ids=110
add bridge=bridge1 tagged=ether1,ether3 vlan-ids=200
add bridge=bridge1 tagged=ether1,ether3 vlan-ids=210
add bridge=bridge1 tagged=ether1 untagged=ether4 vlan-ids=300
/interface bridge
set numbers=0 vlan-filtering=yes
/system identity
set name=sw1
/tool romon
set enabled=yes

SW2

/interface bridge
add name=bridge1 vlan-filtering=no
/interface bridge port
add bridge=bridge1 interface=ether1
add bridge=bridge1 hw=no interface=ether2 pvid=400
add bridge=bridge1 hw=no interface=ether3 pvid=500
add bridge=bridge1 hw=no interface=ether4 pvid=600
/interface bridge vlan
add bridge=bridge1 tagged=ether1 untagged=ether2 vlan-ids=400
add bridge=bridge1 tagged=ether1 untagged=ether3 vlan-ids=500
add bridge=bridge1 tagged=ether1 untagged=ether4 vlan-ids=600
/interface bridge
set numbers=0 vlan-filtering=yes
/system identity
set name=sw2
/tool romon
set enabled=yes
```

sw100

```
/interface bridge
add name=bridge1 vlan-filtering=no
/interface bridge port
add bridge=bridge1 interface=ether1
add bridge=bridge1 hw=no interface=ether2 pvid=100
add bridge=bridge1 hw=no interface=ether3 pvid=110
/interface bridge vlan
add bridge=bridge1 tagged=ether1 untagged=ether2 vlan-ids=100
add bridge=bridge1 tagged=ether1 untagged=ether3 vlan-ids=110
/interface bridge
set numbers=0 vlan-filtering=yes
/system identity
set name=sw100
/tool romon
set enabled=yes
```

sw200

```
/interface bridge
add name=bridge1 vlan-filtering=no
/interface bridge port
add bridge=bridge1 interface=ether1
add bridge=bridge1 hw=no interface=ether2 pvid=200
add bridge=bridge1 hw=no interface=ether3 pvid=210
/interface bridge vlan
add bridge=bridge1 tagged=ether1 untagged=ether2 vlan-ids=200
add bridge=bridge1 tagged=ether1 untagged=ether3 vlan-ids=210
/interface bridge
set numbers=0 vlan-filtering=yes
/system identity
set name=sw200
/tool romon
set enabled=yes
```
