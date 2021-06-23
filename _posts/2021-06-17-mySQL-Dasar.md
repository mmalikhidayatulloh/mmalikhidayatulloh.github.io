---
layout: post
---
![](/assets/IMG/cropped-mariadb_org_rgb_v-2.png)

* Do not remove this line (it will not be displayed) 
{:toc}

Tutorial ini merupakan lanjutan dari [WebServer](https://mmalikhidayatulloh.github.io/2021/06/15/WEB-SERVER-Install-dan-Konfigurasi-LAMP-di-Linux-(openSUSE).html).
## Masuk ke database
```
sudo mysql -u root
```
Artinya masuk ke mysql dengan *user* root
## Melihat isi database yang tersedia
```
show databases;
```
## Membuat database
contoh `belajarSQL`
```
create database belajarSQL;
```
## Menggunakan database
```
use belajarSQL
```
## Membuat tabel
misal tabel member
```
create table member (
    -> id int primary key auto_increment,
    -> nama varchar(100),
    -> na char(2),
    -> email varchar(100),
    -> alamat varchar(100),
    -> gambar varchar(100)
    -> );
```
Penjelasan:
* Setelah `(` tekan enter agar muncul tanda `->` kemudian masing-masing data dipisahkan dengan tanda koma `,` untuk data angka ditambahkan `char` selain angka menggunakan `varchar` untuk yang di dalam kurung menyatakan maksimal jumlah karakter. Misal pada data `na` (14) maksudnya angka bebas dengan jumlah digit maksimal `14` misalnya `99999999999999`.
* `id` itu seperti nomor urut
* `na` maksudnya nomor anggota
* di akhir beri tanda `);` untuk menutup
## Melihat semua tabel yang tersedia
```
show tables
```
## Melihat isi tabel
```
describe belajarSQL
```
## Menginput data
Pastikan sesuai urutan yang telah dibuat, contoh berdasarkan tabel yang saya buat
```
insert into belajarSQL values ('', 'Mamal', `11`, 'mamal@email.com', 'Cilacap', 'mamal.jpg');
```
Keterangan: untuk ` ``,` maksudnya otomatis akan terisi sesuai urutan data yang diinput, tetapi jika tidak otomatis ya input angka manual.
## Melihat seluruh data pada tabel 
```
select * from belajarSQL;
```
## Melihat parameter tertentu
```
select nama, email from belajarSQL;
```
## Melihat data dengan satu indikator
```
select * from belajarSQL where na ='11';
```
## Mengubah isi data
```
update belajarSQL set nama = 'malik' where na = 11;
```
## Menghapus data tertentu
```
delete from belajarSQL where na = '11';
```
## Menghapus tabel
```
drop table belajarSQL;
```
