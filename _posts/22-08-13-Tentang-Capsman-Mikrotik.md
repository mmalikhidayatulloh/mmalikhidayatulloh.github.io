CAPsMAN untuk memanage banyak AP secara terpusat karena umumnya untuk mengatur AP itu harus dikonfig manual di masing-masing AP. Nah dengan adanya CAPsMAN maka konfigurasi bisa dilakukan secara terpusat.

Syarat:
* Ada yang bertidak sebagai manager, biasanya router dan sebagai manager tidak harus punya interface wlan tapi harus punya package wireless karena fitur capsman ada di package wireless
* Ada yang bertindak sebagai cAP. Boleh cAP, cAP lite, hAP, yang penting perangkat mikrotik yang punya interface wlan

Dasar-dasarnya:

# 1. Aktifkan CAPsMAN manager
remote router yang akan menjadi manager dengan winbox
```
winbox>capman>manager>enable
```
# 2. Konfigurasi cAP
remote cAP dengan winbox
```
winbox>wireless>cap>enable>interface:wlan>Discovery interface:ether1
```
discovery interface, anda pilih interface mana yang menghubungkan antara cap dengan manager. bila tidak satu segmen/melewati jalur routing maka masukkan ip manager

# 3. Konfig dasar
cap akan otomatis terdeteksi oleh capsman dan bisa langsung dikonfigurasi
```
wiress>mode:ap>SSID:nama wifi>channel>frekuensi:2412>channel width:20MHz>Band:2ghz-b/g/n>datapath>bridge:bridge-LAN>Apply
```
# 4. Fitur
## 1. Provioning
## 2. Access list
