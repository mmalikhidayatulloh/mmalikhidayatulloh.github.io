DNS (domain name system) diperlukan untuk merubah nama domain dan nama host menjadi alamat IP. Dengan cara ini, alamat IP 192.168.2.100 ditetapkan ke host dengan nama `localhost` (biasanya hostname default localhost).

# Terminologi DNS

## Zone

Ruang nama domain dibagi menjadi wilayah yang disebut `zone`. Misalnya, jika Anda memiliki `example.com` , Anda memiliki bagian `example` (sebagai zone) dari domain com.

## DNS Server

DNS Server adalah server yang memelihara nama dan informasi IP untuk sebuah domain. Anda dapat memiliki server DNS utama untuk master zone, server sekunder untuk slave zone, atau slave zone tanpa zone untuk caching.

* Server DNS master zone

    Master zone mencakup semua host dari jaringan Anda dan Server DNS master zone menyimpan catatan terbaru untuk semua host di domain Anda.

* Server DNS slave zone
    
    Slave zone adalah salinan dari master zone. Server DNS slave zone memperoleh data zonanya dengan operasi transfer zona dari server masternya. Server DNS slave zone merespons secara otoritatif untuk zona tersebut selama memiliki data zona yang valid (tidak kedaluwarsa). Jika slave zone tidak dapat memperoleh salinan baru dari data zona, ia berhenti merespons untuk zona tersebut.

## Forwarder

Forwarder adalah tempat server DNS Anda harus mengirim pertanyaan yang tidak dapat dijawabnya. Untuk mengaktifkan sumber konfigurasi yang berbeda dalam satu konfigurasi, gunakan `netconfig`

## Record

Record adalah informasi tentang nama dan alamat IP. Catatan yang didukung dan sintaksnya dijelaskan dalam dokumentasi BIND. Beberapa record khusus adalah:
* NS Record

    NS Record memberi tahu server nama mesin mana yang bertanggung jawab atas zona domain tertentu.
* MX Record

    MX Record (pertukaran surat) menjelaskan mesin yang harus dihubungi untuk mengarahkan surat melalui Internet.
* SOA Record

    SOA (Start of Authority) Record adalah record pertama dalam file zona. SOA Record digunakan saat menggunakan DNS untuk menyinkronkan data antara beberapa komputer.

# Install

Untuk menginstal DNS Server, ***Buka YaST*** dan pilih ***Software > Software Management***. Pilih ***View Patterns*** dan pilih ***DHCP and DNS Server***. Konfirmasi penginstalan dependensi paket untuk menyelesaikan proses penginstalan.
Atau gunakan perintah berikut pada terminal:
```
$ sudo zypper in -t pattern dhcp_dns_server
```

# Konfigurasi menggunakan YaST

Gunakan modul DNS YaST untuk mengongurasi DNS Server untuk jaringan lokal. Saat memulai modul untuk pertama kalinya, ketika wizard dimulai, Anda diminta untuk membuat beberapa keputusan tentang administrasi server. Menyelesaikan pengaturan awal ini menghasilkan konfigurasi server dasar. Gunakan `Expert mode` untuk menangani tugas konfigurasi yang lebih lanjut, seperti mengatur ACL, logging, TSIG Keys, dan opsi lainnya.

## Konfigurasi Wizard

Wizard terdiri dari tiga langkah atau dialog. Di tempat yang sesuai dalam dialog, Anda dapat memasuki konfigurasi `Expert mode`

1. Saat memulai modul untuk pertama kalinya, dialog Pengaturan Forwarder terbuka. *Local DNS Resolution Policy* memungkinkan untuk mengatur opsi berikut:

    * Merging forwarders is disabled
    * Automatic merging
    * Merging forwarders is enabled
    * Custom configuration — Jika Custom configuration dipilih, *Custom Policy* dapat ditentukan; secara default (dengan memilih *Automatic merging*), *Custom Policy* disetel ke `auto`, tetapi di sini Anda dapat menyetel nama interface atau memilih dari dua nama Policy special: STATIC dan STATIC_FALLBACK.

    Di *Local DNS Resolution Forwarder*, tentukan layanan mana yang akan digunakan: *Using system name servers, This name server (bind)*, atau *Local dnsmasq server*.
    
    Untuk informasi lebih lanjut tentang semua pengaturan ini, lihat **man netconfig**.

    Forwarder adalah server DNS tempat server DNS Anda mengirimkan kueri yang tidak dapat dijawabnya sendiri. Masukkan alamat IP  dan klik *Add*