## RESET MODEM
tekan lama tombol reset

## Login
Perhatikan informasi SSID dan Password Wifi di belakang perangkat
```
akses web 192.168.1.1
Username : admin
Password : Telkomdso123
```
>ada beberapa moden ZTE yang loginnya
>>username:user password:user

## Setup sumber internet
```
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
```
Jika ingin semua port bisa digunakan untuk menerima sumber internet
```
Network>WAN>Port Binding
centang semua
```

## Aktifkan WiFi
```
Network>WLAN
-Enabled
-Enable Isolation: centang
SUBMIT
```
```
Network>WLAN>SSID Settings
Chose SSID: SSID1/2/3/4
SSID Name: isi nama wifinya terserah
Enable SSID: centang
Maximum clients: 32
Priority: 0
SUBMIT
```
```
Network>WLAN>Security
Choose SSID: SSID1/2/3/4
Autentication Type: WPA/WPA2-PSK
WPA Passphrase: isi password untuk wifi
WPA Encription Algoritm: TKIP+AES
SUBMIT
```
## Setup LAN
```
LAN>DHCP Server
LAN IP Address: 192.168.88.1
Subnet Mask: 255.255.255.0
Enble DHCP Server: Ceklist
DHCP Start IP Address: 192.168.88.2
DHCP End IP Address: 192.168.88.254
Assign IspDNS: biarkan saja
DHCP Server 1 IP Address: 192.168.88.1
Default Gateway: 192.168.88.1
SUBMIT
#IPv4 bisa dicustom
```
