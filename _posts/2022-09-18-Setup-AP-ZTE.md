```
RESET MODEM
tekan lama tombol reset

Perhatikan informasi SSID dan Password Wifi di belakang perangkat

akses web 192.168.1.1
Username : admin
Password : Telkomdso123

Network>WAN>WAN Connection
Connection name: create WAN connection
New connection name: isi terserah
enable vlan: biarkan kosong
type: route
service list: internet
MTU: biarkan default
link type: IP
IP version: IPv4
IP Type: DHCP
Enable NAT: ceklist
Create

Network>WAN>Port Binding
centang semua

Network>WLAN
-Enabled
-Enable Isolation: centang
SUBMIT

Network>WLAN>SSID Settings
Chose SSID: SSID1/2/3/4
SSID Name: isi terserah
Enable SSID: centang
Maximum clients: 32
Priority: 0
SUBMIT

Network>WLAN>Security
Choose SSID: SSID1/2/3/4
Autentication Type: WPA/WPA2-PSK
WPA Passphrase: isi password untuk wifi
WPA Encription Algoritm: TKIP+AES
SUBMIT

LAN>DHCP Server
LAN IP Address: 192.168.1.1
Subnet Mask: 255.255.255.0
Enble DHCP Server: Ceklist
DHCP Start IP Address: 192.168.1.2
DHCP End IP Address: 192.168.1.252
Assign IspDNS: biarkan saja
DHCP Server 1 IP Address: 192.168.1.1
Default Gateway: 192.168.1.1
SUBMIT
#IPv4 bisa dicustom
```
