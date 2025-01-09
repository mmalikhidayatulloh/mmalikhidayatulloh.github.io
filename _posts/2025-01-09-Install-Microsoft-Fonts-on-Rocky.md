```
sudo dnf install rpm-build cabextract ttmkfdir
cd /tmp
wget http://corefonts.sourceforge.net/msttcorefonts-2.5-1.spec
rpmbuild -bb msttcorefonts-2.5-1.spec
cp ~/rpmbuild/RPMS/noarch/msttcorefonts-2.5-1.noarch.rpm /tmp
sudo dnf install msttcorefonts-2.5-1.noarch.rpm
sudo fc-cache /usr/share/fonts
```
