ncurses adalah pustaka pemrograman yang menyediakan antarmuka pemrograman aplikasi yang memungkinkan pemrogram untuk menulis antarmuka pengguna berbasis teks dengan cara terminal-independen. Ini adalah toolkit untuk mengembangkan perangkat lunak aplikasi "mirip GUI" yang berjalan di bawah emulator terminal.

X Server atau X.org Server adalah implementasi open source dari X Windows System atau lebih dikenal dengan X11. X11 sendiri adalah sebuah display server yang mengatur interaksi komponen pada antarmuka (GUI). Contohnya interaksi antara mouse atau keyboard dengan window, resize window, memindahkan window dan lain-lain.

Antarmuka YaST(Yet Another Setup Tools) pseudo-grafis berbasis ncurses dirancang terutama untuk membantu administrator sistem mengelola sistem tanpa server X. Antarmuka menawarkan beberapa keunggulan dibandingkan dengan GUI konvensional. Anda dapat menavigasi antarmuka ncurses menggunakan keyboard, dan ada pintasan keyboard untuk hampir semua elemen antarmuka. Antarmuka ncurses ringan pada sumber daya, dan berjalan cepat bahkan pada perangkat keras sederhana. Anda dapat menjalankan versi YaST berbasis ncurses melalui koneksi SSH, sehingga Anda dapat mengelola sistem jarak jauh. Ingatlah bahwa ukuran minimum emulator terminal yang didukung untuk menjalankan YaST adalah 80x25 karakter.

Untuk meluncurkan versi YaST berbasis ncurses, buka terminal dan jalankan perintah 

```
sudo yast2
```

Gunakan tombol `Tab` maupun `tombol navigasi` untuk berpindah-pindah di antara elemen antarmuka seperti item menu, bidang, dan tombol. Semua item menu dan tombol di YaST dapat diakses menggunakan tombol fungsi atau pintasan keyboard yang sesuai. Misalnya, Anda dapat membatalkan operasi saat ini dengan menekan `F9` , sedangkan tombol `F10` dapat digunakan untuk menerima perubahan. Setiap item menu dan tombol di antarmuka berbasis ncurses YaST memiliki huruf yang disorot di labelnya. Huruf ini adalah bagian dari pintasan keyboard yang ditetapkan ke elemen antarmuka. Misalnya, huruf Q disorot di tombol Keluar. Ini berarti Anda dapat mengaktifkan tombol dengan menekan `Alt` misalnya `Alt+Q`

>**Tips:** Jika dialog YaST corrupt atau terdistorsi (misalnya, saat mengubah ukuran jendela), tekan `Ctrl – L` untuk menyegarkan dan memulihkan kontennya.

# Navigasi dalam modul

Deskripsi elemen kontrol berikut dalam modul YaST mengasumsikan bahwa semua tombol fungsi dan kombinasi tombol `Alt` berfungsi dan tidak ditetapkan ke fungsi global yang berbeda.

* Berpindah di antara tombol dan daftar pilihan

    Gunakan `→|` untuk berpindah di antara tombol dan bingkai yang berisi daftar pilihan. Untuk menavigasi ke arah yang berlawanan, gunakan kombinasi `Alt – →|` atau `Shift – →|`.

* Menavigasi dalam daftar pilihan

    Gunakan tombol panah ( ↑ dan ↓ ) untuk berpindah melalui elemen individual dalam bingkai aktif yang berisi daftar pilihan. Jika entri individual lebih panjang dari lebar bingkai, gunakan `Shift – →` atau `Shift – ← `untuk menggulir secara horizontal. Jika tombol panah menyebabkan pilihan berpindah ke bingkai lain, gunakan `Ctrl – E` atau `Ctrl – A` sebagai gantinya.

* Bekerja dengan tombol, tombol radio, dan kotak centang

    Untuk memilih item dengan tanda kurung siku kosong (kotak centang) atau tanda kurung kosong (tombol radio), tekan `Spasi` atau `Enter` . Atau, tombol radio dan kotak centang dapat dipilih secara langsung dengan `Alt – huruf yang disorot`. Dalam hal ini, Anda tidak perlu mengonfirmasi dengan `Enter` . Jika Anda menavigasi ke item dengan `→|`, tekan Enter untuk menjalankan tindakan yang dipilih atau mengaktifkan item menu terkait.

* Tombol fungsi

    Tombol fungsi (dari `F1` hingga `F12` ) memungkinkan akses cepat ke berbagai tombol. Kombinasi tombol fungsi yang tersedia ( FX ) ditampilkan di bagian bawah layar YaST. Tombol fungsi mana yang sebenarnya dipetakan ke tombol mana yang bergantung pada modul YaST yang aktif, karena modul yang berbeda menawarkan tombol yang berbeda (Rincian, Info, Tambah, Hapus, dll.). Gunakan `F10` untuk Terima, OK, Berikutnya, dan Selesai. Tekan `F1` untuk mengakses bantuan YaST.

* Gunakan struktur navigasi

    Beberapa modul YaST menggunakan struktur navigasi di bagian kiri jendela untuk memilih dialog konfigurasi. Gunakan tombol panah (↑ dan ↓) untuk menavigasi di struktur. Gunakan `Spasi` untuk membuka atau menutup item pohon. Dalam mode ncurses, `Enter` harus ditekan setelah pemilihan di pohon navigasi untuk menampilkan dialog yang dipilih. Ini adalah perilaku yang disengaja untuk menghemat penggambaran ulang yang memakan waktu saat menelusuri pohon navigasi.

* Memilih perangkat lunak dalam modul instalasi perangkat lunak

    Gunakan filter di sisi kiri untuk membuat daftar paket yang cocok dengan string yang ditentukan. Paket yang diinstal ditandai dengan huruf `i` . Untuk mengubah status paket, tekan `Spasi` atau `Enter` . Atau, gunakan menu Action untuk memilih perubahan status yang diperlukan (instal, hapus, perbarui, tabu, atau kunci).