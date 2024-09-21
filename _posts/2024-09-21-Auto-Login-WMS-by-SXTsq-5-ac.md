#Find Requirements
Example in my WMS login page
```
username
password
WAG-D4-GBL
GPON05-D4-BMK-3
@wmslite.1672821737.000
```
#Script Login by Username and Password

```
# Daftar Variable
:local user "nama"
:local pass "sandi"
:local gwid "WAG-D4-GBL"
:local ether "wlan1-internet"
:local wlan "GPON05-D4-BMK-3"
:local wms "@wmslite.1672821737.000"
:local redirect "https://www.google.com"
# Akhir Variable

:log info "Menjalankan Auto Login ..."
:local ip [/ip address get [/ip address find interface="$ether"] address];
:local ip [put [:pick $ip 0 [:find $ip "/"]]];
:if ([:len $ip] = 0) do={
	:log error ("Interface $ether tidak mendapatkan alamat ip --- mencoba mendapatkan...");
	/ip dhcp-client release [find interface="$ether"];
};
delay 1s

:local mac [/interface get [find name="$ether"] mac-address];
:local gateway [/ip dhcp-client get [find interface="$ether"] gateway];
:log warning "IP Address     : $ip"
:log warning "MAC Address : $mac"
:log warning "IP Gateway    : $gateway"

:log info "Menghubungkan ..."

:local num1 [:pick [/system clock get time] 0] 
:local num2 [:pick [/system clock get time] 1] 
:local num3 [:pick [/system clock get time] 3] 
:local num4 [:pick [/system clock get time] 6] 
:local char1 [:pick "abcdefghijklmnopqrstuvwxyz" "$num1$num2"]
:local char2 [:pick "abcdefghijklmnopqrstuvwxyz" "2$num2"]
:local char3 [:pick "abcdefghijklmnopqrstuvwxyz" "1$num4"]
:local user "$user.$char3$char1$char2$wms"

:do {
	:tool fetch mode=https http-header-field="Content-Type: application/x-www-form-urlencoded; charset=UTF-8,User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36,Referer: https://welcome2.wifi.id/login/?gw_id=$gwid&client_mac=$mac&wlan=$wlan&sessionid=0803FFFF780244ED-6176D0B2&redirect=$redirect" http-method=post http-data="username=$user&password=$pass" url="https://welcome2.wifi.id/wms/auth/authnew/autologin/quarantine.php\?ipc=$ip&gw_id=$gwid&mac=$mac&redirect=$redirect&wlan=$wlan" dst-path=wms.txt;
	:if ([/ping address=$gateway interface="$ether" count=2] = 0) do={
		:log error "Login gagal... ";
		/ip dhcp-client release [find interface="$ether"];
	}
	:if ([/ping address=$gateway  interface="$ether" count=2] != 0) do={
		:log info "Login SUKSES..."
		:local iRes [/file get wms.txt contents];
		:log warning $iRes
		delay 1s
		:file remove wms.txt
	}
}
#:log warning "$user.$char3$char1$char2$wms"
```
#Script Login WMS Without Username and Password
```
# Daftar Variable
:local pass "sandi"
:local gwid "WAG3-D4-GBL"
:local ether "wlan1"
:local wlan "GPON05-D4-BMK-3"
:local wms "@wmslite.1714274430.000"
:local redirect "https://www.google.com"
# Akhir Variable

:log info "Menjalankan Auto Login ..."
:local ip [/ip address get [/ip address find interface="$ether"] address];
:local ip [put [:pick $ip 0 [:find $ip "/"]]];
:if ([:len $ip] = 0) do={
	:log error ("Interface $ether tidak mendapatkan alamat ip --- mencoba mendapatkan...");
	/ip dhcp-client release [find interface="$ether"];
};
delay 1s

:local mac [/interface get [find name="$ether"] mac-address];
:local gateway [/ip dhcp-client get [find interface="$ether"] gateway];
:log warning "IP Address     : $ip"
:log warning "MAC Address : $mac"
:log warning "IP Gateway    : $gateway"

:log info "Menghubungkan ..."

:local num1 [:pick [/system clock get time] 0] 
:local num2 [:pick [/system clock get time] 1] 
:local num3 [:pick [/system clock get time] 3] 
:local num4 [:pick [/system clock get time] 6] 
:local char1 [:pick "abcdefghijklmnopqrstuvwxyz" "$num1$num2"]
:local char2 [:pick "abcdefghijklmnopqrstuvwxyz" "2$num2"]
:local char3 [:pick "abcdefghijklmnopqrstuvwxyz" "1$num4"]
:local user "$user.$char3$char1$char2$wms"

:do {
	:tool fetch mode=https http-header-field="Content-Type: application/x-www-form-urlencoded; charset=UTF-8,User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36,Referer: https://welcome2.wifi.id/login/?gw_id=$gwid&client_mac=$mac&wlan=$wlan&sessionid=FF24000378028370-6312F7A9&redirect=$redirect" http-method=post http-data="username=$pass.hjk9$wms&password=$pass" url="https://welcome2.wifi.id/wms/auth/authnew/autologin/quarantine.php\?ipc=$ip&gw_id=$gwid&mac=$mac&redirect=$redirect&wlan=$wlan" dst-path=wms.txt;
	:if ([/ping address=$gateway interface="$ether" count=2] = 0) do={
		:log error "Login gagal... ";
		/ip dhcp-client release [find interface="$ether"];
	}
	:if ([/ping address=$gateway  interface="$ether" count=2] != 0) do={
		:log info "Login SUKSES..."
		:local iRes [/file get wms.txt contents];
		:log warning $iRes
		delay 1s
		:file remove wms.txt
	}
}
:log warning "$user.$char3$char1$char2$wms"
```
#Scheduler
```
:if ([:ping 8.8.8.8 interface=wlan1 count=5]=0) do={:system script run wms;}
```
