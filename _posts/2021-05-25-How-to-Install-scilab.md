---
layout: post
---
![Gambar](https://www.scilab.org/sites/all/themes/scilab/images/scilab-logo.png)

* Do not remove this line (it will not be displayed) 
{:toc}

>Scilab is Free and Open Source software for numerical computation providing a powerful computing environment for engineering and scientific applications.

### Visit [Scilab website](https://www.scilab.org/download/) and choose GNU/Linux 64 bits
### Downloads `.tar.gz` file
### Go to your downloads folder
```
cd Downloads
```
### Convert file `.tar.gz`
```
tar xzvf scilab-version.bin.linux-x86_64.tar.gz
```
### Go to scilab directory
```
cd scilab-version
```
### Run this command
```
sudo zypper in ncurses5
```
```
sudo ln -s /usr/lib/libtinfo.so.6 /usr/lib/libtinfo.so.5
```
### Run scilab with command
```
./bin/scilab
```
## Result
![image](/assets/IMG/Screenshot_2021-05-25_12-29-43.png)

[BACK](./index.md)
