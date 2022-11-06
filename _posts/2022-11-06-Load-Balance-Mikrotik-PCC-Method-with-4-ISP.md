I use RB2011UiAS-RM, ether6,7,8,9 (fast ethernet) as dhcp-client from ISP. ether4 (gigabit ethernet) as dhcp-server/LAN



```
/ip dhcp-client
add interface=ether1
add disabled=no interface=ether6
add disabled=no interface=ether7
add disabled=no interface=ether8
add disabled=no interface=ether9
/interface bridge
add name=bridge-int
/interface bridge port
add bridge=bridge-int interface=ether4
/ip address
add address=192.168.100.1/24 interface=bridge-int network=192.168.100.0
/ip pool
add name=dhcp ranges=192.168.100.2-192.168.100.254
/ip dhcp-server
add address-pool=dhcp disabled=no interface=bridge-int name=dhcp1
/interface list
add name=WAN
add name=LAN
/interface list member
add interface=bridge-int list=LAN
add interface=ether6 list=WAN
add interface=ether7 list=WAN
add interface=ether8 list=WAN
add interface=ether9 list=WAN
/ip dhcp-server network
add address=192.168.100.0/24 gateway=192.168.100.1 netmask=8
/ip firewall mangle
add action=accept chain=prerouting dst-address=192.168.1.0/24 in-interface=bridge-int
add action=accept chain=prerouting dst-address=192.168.2.0/24 in-interface=bridge-int
add action=accept chain=prerouting dst-address=192.168.3.0/24 in-interface=bridge-int
add action=accept chain=prerouting dst-address=192.168.4.0/24 in-interface=bridge-int
add action=mark-connection chain=prerouting connection-mark=no-mark in-interface=ether6 new-connection-mark=koneksi-1
add action=mark-connection chain=prerouting connection-mark=no-mark in-interface=ether7 new-connection-mark=koneksi-2
add action=mark-connection chain=prerouting connection-mark=no-mark in-interface=ether8 new-connection-mark=koneksi-3
add action=mark-connection chain=prerouting connection-mark=no-mark in-interface=ether9 new-connection-mark=koneksi-4
add action=mark-connection chain=prerouting comment="Per Connection Classifier" connection-mark=no-mark dst-address-type=!local \
    in-interface=bridge-int new-connection-mark=koneksi-1 passthrough=yes per-connection-classifier=both-addresses-and-ports:4/0
add action=mark-connection chain=prerouting connection-mark=no-mark dst-address-type=!local in-interface=bridge-int \
    new-connection-mark=koneksi-2 passthrough=yes per-connection-classifier=both-addresses-and-ports:4/1
add action=mark-connection chain=prerouting connection-mark=no-mark dst-address-type=!local in-interface=bridge-int \
    new-connection-mark=koneksi-3 passthrough=yes per-connection-classifier=both-addresses-and-ports:4/2
add action=mark-connection chain=prerouting connection-mark=no-mark dst-address-type=!local in-interface=bridge-int \
    new-connection-mark=koneksi-4 passthrough=yes per-connection-classifier=both-addresses-and-ports:4/3
add action=mark-routing chain=prerouting connection-mark=koneksi-1 in-interface=bridge-int new-routing-mark=mangle-1 passthrough=\
    yes
add action=mark-routing chain=prerouting connection-mark=koneksi-2 in-interface=bridge-int new-routing-mark=mangle-2 passthrough=\
    yes
add action=mark-routing chain=prerouting connection-mark=koneksi-3 in-interface=bridge-int new-routing-mark=mangle-3 passthrough=\
    yes
add action=mark-routing chain=prerouting connection-mark=koneksi-4 in-interface=bridge-int new-routing-mark=mangle-4 passthrough=\
    yes
add action=mark-routing chain=output comment=OUTPUT connection-mark=koneksi-1 new-routing-mark=mangle-1 passthrough=yes
add action=mark-routing chain=output connection-mark=koneksi-2 new-routing-mark=mangle-2
add action=mark-routing chain=output connection-mark=koneksi-3 new-routing-mark=mangle-3
add action=mark-routing chain=output connection-mark=koneksi-4 new-routing-mark=mangle-4
/ip firewall nat
add action=masquerade chain=srcnat out-interface-list=WAN
/ip route
add check-gateway=ping distance=1 gateway=192.168.1.1 routing-mark=mangle-1
add check-gateway=ping distance=1 gateway=192.168.2.1 routing-mark=mangle-2
add check-gateway=ping distance=1 gateway=192.168.3.1 routing-mark=mangle-3
add check-gateway=ping distance=1 gateway=192.168.4.1 routing-mark=mangle-4
add check-gateway=ping distance=1 gateway=192.168.1.1
add check-gateway=ping distance=2 gateway=192.168.2.1
add check-gateway=ping distance=3 gateway=192.168.3.1
add check-gateway=ping distance=4 gateway=192.168.4.1
/system clock
set time-zone-name=Asia/Jakarta
/system scheduler
add interval=1d name="auto reboot" on-event="/system reboot" start-date=nov/06/2022 start-time=02:00:00
/tool romon
set enabled=yes
```
