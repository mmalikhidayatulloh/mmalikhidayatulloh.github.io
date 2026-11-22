## cek versi python
```
!python --version
```
dalam kasus saya yang trouble adalah 'python3.11.13' dan ketika saya mencoba fedora di podman menggunakan `python3.13` work. jadi dalam hal ini saya akan menginstall `python3.13`
## install versi yang tidak trouble
```
!apt update;apt install python3.13 -y
```
## buang versi sebelumnya
```
!apt purge python3.10 python3.11 -y;apt autoremove
```
## update
```
!sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.13 1
```
## cek lagi
```
!python3 --version
```
## install pip manual
pake laptop offline anda
```
wget https://bootstrap.pypa.io/get-pip.py
```
upload ke kaggle
## install pip
```
!python get-pip.py
```
## install docling
```
!pip install docling
```
## gunakan docling
```
!docling --to html --pipeline vlm --vlm-model granite_docling "/kaggle/input/pdfkui/1_K Byrappa_ Masahiro Yoshimura - Handbook of hydrothermal technology (2013 William Andrew).pdf"
```
jika masih trouble gunakan accelerator lain
