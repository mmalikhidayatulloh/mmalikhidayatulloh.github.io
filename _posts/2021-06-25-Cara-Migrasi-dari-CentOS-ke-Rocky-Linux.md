---
layout: post
---
![rocky](/assets/IMG/rocky.png)

* Do not remove this line (it will not be displayed) 
{:toc}

Setelah adanya berita dari RedHat bahwa centos tidak akan dilanjutkan kembali setelah desember 2021 dan akan dialihkan ke centos stream maka user centos banyak yang kecewa dengan keputusan ini sehinnga beberapa user ada yang mulai migrasi ke debian maupun openSUSE dan developer ada yang membuat gerakan untuk mengatasi kekecewaan tersebut dengan membuat distro linux yang baru yang kompatibel dengan RedHat, diawali oleh Alma Linux yang langsung launching tidak lama setelah adanya kebijakan baru RedHat tersebut. Kemudian di belahan dunia yang lain sebuah project distro linux pengganti Centos didirikan oleh seseorang yang dulunya pernah menjadi pendiri centos, projectnya bernama `Rocky linux`. Pada bulan juni 2021 rocky linux rilis untuk pertama kalinya dan di sini saya akan mencoba mendemonstrasikan cara untuk migrasi dari Centos ke Rocky linux.

# 1. Pastikan CentOS dalam kondisi update
```
sudo dnf update && sudo dnf upgrade
```
# 2. Migrasi
* Downlod script untuk migrasi ke Rocky linux
```
curl -O https://raw.githubusercontent.com/rocky-linux/rocky-tools/main/migrate2rocky/migrate2rocky.sh
```
* Edit Hak Akses Agar Bisa dijalankan
```
sudo chmod +x migrate2rocky.sh
```
* Jalankan script migrasinya
```
sudo ./migrate2rocky.sh -r
```
>Penjelasan
```
./migrate2rocky.sh -h
├── -h   # --> Display this help
├── -r   # --> Convert to Rocky
└── -V   # --> Verify switch
```
* Outputnya seperti ini
```
Getting a list of enabled modules for the system repositories.

In addition to the above the following system packages will be removed:
centos-linux-release
centos-linux-release

Excluding modules:
libselinux-python:2.8

Found the following modules to re-enable at completion:
container-tools:rhel8

Added rockyappstream repo from https://dl.rockylinux.org/pub/rocky/8/AppStream/x86_64/os/
Added rockybaseos repo from https://dl.rockylinux.org/pub/rocky/8/BaseOS/x86_64/os/
rockyappstream                                  1.8 MB/s | 7.1 MB     00:03    
rockybaseos                                     998 kB/s | 2.5 MB     00:02    
Last metadata expiration check: 0:00:01 ago on Fri 25 Jun 2021 02:38:14 AM WIB.
> > > ================================================================================
 Package                  Arch       Version              Repository       Size
================================================================================
Installing:
 rocky-gpg-keys           noarch     8.4-26.el8           rockybaseos      11 k
 rocky-logos              x86_64     84.5-7.el8           rockybaseos     326 k
 rocky-release            noarch     8.4-26.el8           rockybaseos      19 k
 rocky-repos              noarch     8.4-26.el8           rockybaseos      12 k
Removing:
 centos-gpg-keys          noarch     1:8-2.el8            @baseos         3.3 k
 centos-linux-release     noarch     8.4-1.2105.el8       @baseos          25 k
 centos-linux-repos       noarch     8-2.el8              @baseos          26 k
 centos-logos             x86_64     85.5-1.el8           @baseos         698 k

Transaction Summary
================================================================================
Install  4 Packages
Remove   4 Packages

Total download size: 368 k
Downloading Packages:
(1/4): rocky-gpg-keys-8.4-26.el8.noarch.rpm      31 kB/s |  11 kB     00:00    
(2/4): rocky-repos-8.4-26.el8.noarch.rpm        108 kB/s |  12 kB     00:00    
(3/4): rocky-logos-84.5-7.el8.x86_64.rpm        611 kB/s | 326 kB     00:00    
warning: (4/4): rocky-release-8.4-26.el8.noarch.rpm       34 kB/s |  19 kB     00:00    
--------------------------------------------------------------------------------
Total                                           629 kB/s | 368 kB     00:00     
/var/cache/dnf/rockybaseos-56e41edc159a87c2/packages/rocky-gpg-keys-8.4-26.el8.noarch.rpm: Header V4 RSA/SHA256 Signature, key ID 6d745a60: NOKEY
rockybaseos                                     1.6 MB/s | 1.6 kB     00:00    
Importing GPG key 0x6D745A60:
 Userid     : "Release Engineering <infrastructure@rockylinux.org>"
 Fingerprint: 7051 C470 A929 F454 CEBE 37B7 15AF 5DAC 6D74 5A60
 From       : /tmp/tmp.vU1PggZX4n/gpg/RPM-GPG-KEY-rockyofficial
Key imported successfully
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                                                        1/1 
  Running scriptlet: rocky-gpg-keys-8.4-26.el8.noarch                       1/1 
  Installing       : rocky-gpg-keys-8.4-26.el8.noarch                       1/8 
  Installing       : rocky-release-8.4-26.el8.noarch                        2/8 
  Installing       : rocky-repos-8.4-26.el8.noarch                          3/8 
  Installing       : rocky-logos-84.5-7.el8.x86_64                          4/8 
  Running scriptlet: rocky-logos-84.5-7.el8.x86_64                          4/8 
  Erasing          : centos-linux-release-8.4-1.2105.el8.noarch             5/8 
  Erasing          : centos-linux-repos-8-2.el8.noarch                      6/8 
  Erasing          : centos-gpg-keys-1:8-2.el8.noarch                       7/8 
  Erasing          : centos-logos-85.5-1.el8.x86_64                         8/8 
  Running scriptlet: centos-logos-85.5-1.el8.x86_64                         8/8 
  Running scriptlet: rocky-logos-84.5-7.el8.x86_64                          8/8 
  Running scriptlet: centos-logos-85.5-1.el8.x86_64                         8/8 
  Verifying        : rocky-gpg-keys-8.4-26.el8.noarch                       1/8 
  Verifying        : rocky-logos-84.5-7.el8.x86_64                          2/8 
  Verifying        : rocky-release-8.4-26.el8.noarch                        3/8 
  Verifying        : rocky-repos-8.4-26.el8.noarch                          4/8 
  Verifying        : centos-gpg-keys-1:8-2.el8.noarch                       5/8 
  Verifying        : centos-linux-release-8.4-1.2105.el8.noarch             6/8 
  Verifying        : centos-linux-repos-8-2.el8.noarch                      7/8 
  Verifying        : centos-logos-85.5-1.el8.x86_64                         8/8 

Installed:
  rocky-gpg-keys-8.4-26.el8.noarch         rocky-logos-84.5-7.el8.x86_64        
  rocky-release-8.4-26.el8.noarch          rocky-repos-8.4-26.el8.noarch        
Removed:
  centos-gpg-keys-1:8-2.el8.noarch   centos-linux-release-8.4-1.2105.el8.noarch 
  centos-linux-repos-8-2.el8.noarch  centos-logos-85.5-1.el8.x86_64             

Complete!
Last metadata expiration check: 0:00:06 ago on Fri 25 Jun 2021 02:38:14 AM WIB.
> Leaving Shell

Removing dnf cache
Ensuring repos are enabled before the package swap
Enabling modules

Rocky Linux 8 - AppStream                       1.2 MB/s | 7.1 MB     00:05    
Rocky Linux 8 - BaseOS                          1.1 MB/s | 2.5 MB     00:02    
Rocky Linux 8 - Extras                          2.3 kB/s | 2.7 kB     00:01    
Dependencies resolved.
Nothing to do.
Complete!
Disabling excluded modules

Last metadata expiration check: 0:00:02 ago on Fri 25 Jun 2021 02:38:37 AM WIB.
Only module name is required. Ignoring unneeded information in argument: 'libselinux-python:2.8'
Dependencies resolved.
================================================================================
 Package           Architecture     Version             Repository         Size
================================================================================
Disabling modules:
 libselinux-python                                                             

Transaction Summary
================================================================================

Complete!

Syncing packages

Last metadata expiration check: 0:00:03 ago on Fri 25 Jun 2021 02:38:37 AM WIB.
Dependencies resolved.
====================================================================================================
 Package                          Arch    Version                                   Repo        Size
====================================================================================================
Installing:
 kernel                           x86_64  4.18.0-305.3.1.el8_4                      baseos     5.9 M
 kernel-core                      x86_64  4.18.0-305.3.1.el8_4                      baseos      36 M
 kernel-modules                   x86_64  4.18.0-305.3.1.el8_4                      baseos      28 M
Upgrading:
 acl                              x86_64  2.2.53-1.el8.1                            baseos      80 k
 audit                            x86_64  3.0-0.17.20191104git1c2f876.el8.1         baseos     253 k
 audit-libs                       x86_64  3.0-0.17.20191104git1c2f876.el8.1         baseos     116 k
 bpftool                          x86_64  4.18.0-305.3.1.el8_4                      baseos     6.6 M
 e2fsprogs                        x86_64  1.45.6-1.el8.1                            baseos     1.0 M
 e2fsprogs-libs                   x86_64  1.45.6-1.el8.1                            baseos     232 k
 jimtcl                           x86_64  0.77-6.el8.1                              baseos     224 k
 kernel-tools                     x86_64  4.18.0-305.3.1.el8_4                      baseos     6.1 M
 kernel-tools-libs                x86_64  4.18.0-305.3.1.el8_4                      baseos     5.9 M
 libacl                           x86_64  2.2.53-1.el8.1                            baseos      33 k
 libcom_err                       x86_64  1.45.6-1.el8.1                            baseos      48 k
 libnghttp2                       x86_64  1.33.0-3.el8_3.1                          baseos      76 k
 libreport-filesystem             x86_64  2.9.5-15.el8.rocky.1                      baseos      20 k
 libss                            x86_64  1.45.6-1.el8.1                            baseos      52 k
 ncurses                          x86_64  6.1-7.20180224.el8.1                      baseos     386 k
 ncurses-base                     noarch  6.1-7.20180224.el8.1                      baseos      80 k
 ncurses-libs                     x86_64  6.1-7.20180224.el8.1                      baseos     332 k
 nettle                           x86_64  3.4.1-4.el8_4                             baseos     299 k
 platform-python                  x86_64  3.6.8-37.el8.rocky                        baseos      84 k
 platform-python-pip              noarch  9.0.3-19.el8.rocky                        baseos     1.7 M
 python3-audit                    x86_64  3.0-0.17.20191104git1c2f876.el8.1         baseos      85 k
 python3-libs                     x86_64  3.6.8-37.el8.rocky                        baseos     7.8 M
 python3-perf                     x86_64  4.18.0-305.3.1.el8_4                      baseos     6.0 M
 python3-pip-wheel                noarch  9.0.3-19.el8.rocky                        baseos     1.0 M
 rsyslog                          x86_64  8.1911.0-7.el8.1                          appstream  730 k
 rsyslog-gnutls                   x86_64  8.1911.0-7.el8.1                          appstream   30 k
 rsyslog-gssapi                   x86_64  8.1911.0-7.el8.1                          appstream   32 k
 rsyslog-relp                     x86_64  8.1911.0-7.el8.1                          appstream   31 k
 usb_modeswitch                   x86_64  2.5.2-1.el8.2                             baseos      77 k
 xz                               x86_64  5.2.4-3.el8.1                             baseos     152 k
 xz-libs                          x86_64  5.2.4-3.el8.1                             baseos      93 k
Reinstalling:
 NetworkManager                   x86_64  1:1.30.0-7.el8                            baseos     2.6 M
 NetworkManager-config-server     noarch  1:1.30.0-7.el8                            baseos     127 k
 NetworkManager-libnm             x86_64  1:1.30.0-7.el8                            baseos     1.8 M
 NetworkManager-team              x86_64  1:1.30.0-7.el8                            baseos     144 k
 NetworkManager-tui               x86_64  1:1.30.0-7.el8                            baseos     326 k
 PackageKit                       x86_64  1.1.12-6.el8                              appstream  598 k
 PackageKit-glib                  x86_64  1.1.12-6.el8                              appstream  139 k
 abattis-cantarell-fonts          noarch  0.0.25-6.el8                              appstream  154 k
 adcli                            x86_64  0.8.2-9.el8                               baseos     113 k
 alsa-sof-firmware                noarch  1.6.1-2.el8                               baseos     674 k
 at                               x86_64  3.1.20-11.el8                             baseos      80 k
 attr                             x86_64  2.4.48-3.el8                              baseos      67 k
 authselect                       x86_64  1.2.2-2.el8                               baseos     132 k
 authselect-compat                x86_64  1.2.2-2.el8                               appstream   36 k
 authselect-libs                  x86_64  1.2.2-2.el8                               baseos     221 k
 avahi-libs                       x86_64  0.7-20.el8                                baseos      61 k
 basesystem                       noarch  11-5.el8                                  baseos     9.3 k
 bash                             x86_64  4.4.20-1.el8_4                            baseos     1.5 M
 bash-completion                  noarch  1:2.7-5.el8                               baseos     272 k
 bc                               x86_64  1.07.1-5.el8                              baseos     128 k
 bind-export-libs                 x86_64  32:9.11.26-4.el8_4                        baseos     1.1 M
 bind-libs                        x86_64  32:9.11.26-4.el8_4                        appstream  173 k
 bind-libs-lite                   x86_64  32:9.11.26-4.el8_4                        appstream  1.2 M
 bind-license                     noarch  32:9.11.26-4.el8_4                        appstream  101 k
 bind-utils                       x86_64  32:9.11.26-4.el8_4                        appstream  450 k
 binutils                         x86_64  2.30-93.el8                               baseos     5.8 M
 biosdevname                      x86_64  0.7.3-2.el8                               baseos      43 k
 blktrace                         x86_64  1.2.0-10.el8                              baseos     148 k
 bolt                             x86_64  0.9.1-1.el8                               baseos     200 k
 brotli                           x86_64  1.0.6-3.el8                               baseos     322 k
 bzip2                            x86_64  1.0.6-26.el8                              baseos      59 k
 bzip2-libs                       x86_64  1.0.6-26.el8                              baseos      47 k
 c-ares                           x86_64  1.13.0-5.el8                              baseos      92 k
 ca-certificates                  noarch  2020.2.41-80.0.el8_2                      baseos     390 k
 cairo                            x86_64  1.15.12-3.el8                             appstream  717 k
 cairo-gobject                    x86_64  1.15.12-3.el8                             appstream   32 k
 checkpolicy                      x86_64  2.9-1.el8                                 baseos     345 k
 chkconfig                        x86_64  1.13-2.el8                                baseos     193 k
 chrony                           x86_64  3.5-2.el8                                 baseos     269 k
 clevis                           x86_64  15-1.el8                                  appstream   56 k
 clevis-luks                      x86_64  15-1.el8                                  appstream   36 k
 cockpit                          x86_64  238.2-1.el8                               baseos      75 k
 cockpit-bridge                   x86_64  238.2-1.el8                               baseos     534 k
 cockpit-packagekit               noarch  238.2-1.el8                               appstream  648 k
 cockpit-storaged                 noarch  238.2-1.el8                               appstream  639 k
 cockpit-system                   noarch  238.2-1.el8                               baseos     3.4 M
 cockpit-ws                       x86_64  238.2-1.el8                               baseos     1.3 M
 coreutils                        x86_64  8.30-8.el8                                baseos     1.2 M
 coreutils-common                 x86_64  8.30-8.el8                                baseos     2.0 M
 cpio                             x86_64  2.12-10.el8                               baseos     264 k
 cracklib                         x86_64  2.9.6-15.el8                              baseos      92 k
 cracklib-dicts                   x86_64  2.9.6-15.el8                              baseos     4.0 M
 cronie                           x86_64  1.5.2-4.el8                               baseos     117 k
 cronie-anacron                   x86_64  1.5.2-4.el8                               baseos      40 k
 crontabs                         noarch  1.11-17.20190603git.el8                   baseos      24 k
 crypto-policies                  noarch  20210209-1.gitbfb6bed.el8_3               baseos      61 k
 crypto-policies-scripts          noarch  20210209-1.gitbfb6bed.el8_3               baseos      66 k
 cryptsetup                       x86_64  2.3.3-4.el8                               baseos     189 k
 cryptsetup-libs                  x86_64  2.3.3-4.el8                               baseos     469 k
 cups-libs                        x86_64  1:2.2.6-38.el8                            baseos     432 k
 curl                             x86_64  7.61.1-18.el8                             baseos     352 k
 cyrus-sasl-gssapi                x86_64  2.1.27-5.el8                              baseos      49 k
 cyrus-sasl-lib                   x86_64  2.1.27-5.el8                              baseos     122 k
 cyrus-sasl-plain                 x86_64  2.1.27-5.el8                              baseos      46 k
 dbus                             x86_64  1:1.12.8-12.el8_4.2                       baseos      40 k
 dbus-common                      noarch  1:1.12.8-12.el8_4.2                       baseos      45 k
 dbus-daemon                      x86_64  1:1.12.8-12.el8_4.2                       baseos     239 k
 dbus-glib                        x86_64  0.110-2.el8                               baseos     126 k
 dbus-libs                        x86_64  1:1.12.8-12.el8_4.2                       baseos     183 k
 dbus-tools                       x86_64  1:1.12.8-12.el8_4.2                       baseos      84 k
 dejavu-fonts-common              noarch  2.35-7.el8                                baseos      73 k
 dejavu-sans-mono-fonts           noarch  2.35-7.el8                                baseos     446 k
 desktop-file-utils               x86_64  0.23-8.el8                                appstream   79 k
 device-mapper                    x86_64  8:1.02.175-5.el8                          baseos     374 k
 device-mapper-event              x86_64  8:1.02.175-5.el8                          baseos     269 k
 device-mapper-event-libs         x86_64  8:1.02.175-5.el8                          baseos     268 k
 device-mapper-libs               x86_64  8:1.02.175-5.el8                          baseos     407 k
 device-mapper-multipath          x86_64  0.8.4-10.el8                              baseos     194 k
 device-mapper-multipath-libs     x86_64  0.8.4-10.el8                              baseos     319 k
 device-mapper-persistent-data    x86_64  0.8.5-4.el8                               baseos     467 k
 diffutils                        x86_64  3.6-6.el8                                 baseos     358 k
 dmidecode                        x86_64  1:3.2-8.el8                               baseos      90 k
 dnf                              noarch  4.4.2-11.el8                              baseos     538 k
 dnf-data                         noarch  4.4.2-11.el8                              baseos     150 k
 dnf-plugins-core                 noarch  4.0.18-4.el8                              baseos      68 k
 dos2unix                         x86_64  7.4.0-3.el8                               baseos     240 k
 dosfstools                       x86_64  4.1-6.el8                                 baseos     120 k
 dracut                           x86_64  049-135.git20210121.el8                   baseos     371 k
 dracut-config-rescue             x86_64  049-135.git20210121.el8                   baseos      57 k
 dracut-network                   x86_64  049-135.git20210121.el8                   baseos     104 k
 dracut-squash                    x86_64  049-135.git20210121.el8                   baseos      57 k
 ed                               x86_64  1.14.2-4.el8                              baseos      80 k
 elfutils-debuginfod-client       x86_64  0.182-3.el8                               baseos      64 k
 elfutils-default-yama-scope      noarch  0.182-3.el8                               baseos      48 k
 elfutils-libelf                  x86_64  0.182-3.el8                               baseos     215 k
 elfutils-libs                    x86_64  0.182-3.el8                               baseos     292 k
 emacs-filesystem                 noarch  1:26.1-5.el8                              baseos      68 k
 ethtool                          x86_64  2:5.8-5.el8                               baseos     205 k
 expat                            x86_64  2.2.5-4.el8                               baseos     110 k
 file                             x86_64  5.33-16.el8_3.1                           baseos      76 k
 file-libs                        x86_64  5.33-16.el8_3.1                           baseos     542 k
 filesystem                       x86_64  3.8-3.el8                                 baseos     1.1 M
 findutils                        x86_64  1:4.6.0-20.el8                            baseos     526 k
 firewalld                        noarch  0.8.2-6.el8                               baseos     487 k
 firewalld-filesystem             noarch  0.8.2-6.el8                               baseos      75 k
 fontconfig                       x86_64  2.13.1-3.el8                              baseos     273 k
 fontpackages-filesystem          noarch  1.44-22.el8                               baseos      15 k
 fprintd                          x86_64  1.90.9-2.el8                              appstream  153 k
 fprintd-pam                      x86_64  1.90.9-2.el8                              appstream   27 k
 freetype                         x86_64  2.9.1-4.el8_3.1                           baseos     393 k
 fstrm                            x86_64  0.6.0-3.el8.1                             appstream   28 k
 fuse-common                      x86_64  3.2.1-12.el8                              baseos      20 k
 fuse-libs                        x86_64  2.9.7-12.el8                              baseos     101 k
 fuse3                            x86_64  3.2.1-12.el8                              baseos      49 k
 fuse3-libs                       x86_64  3.2.1-12.el8                              baseos      93 k
 gawk                             x86_64  4.2.1-2.el8                               baseos     1.1 M
 gdbm                             x86_64  1:1.18-1.el8                              baseos     129 k
 gdbm-libs                        x86_64  1:1.18-1.el8                              baseos      59 k
 gdisk                            x86_64  1.0.3-6.el8                               baseos     237 k
 gdk-pixbuf2                      x86_64  2.36.12-5.el8                             baseos     465 k
 geolite2-city                    noarch  20180605-1.el8                            appstream   19 M
 geolite2-country                 noarch  20180605-1.el8                            appstream  1.0 M
 gettext                          x86_64  0.19.8.1-17.el8                           baseos     1.1 M
 gettext-libs                     x86_64  0.19.8.1-17.el8                           baseos     309 k
 glib-networking                  x86_64  2.56.1-1.1.el8                            baseos     153 k
 glib2                            x86_64  2.56.4-10.el8_4                           baseos     2.5 M
 glibc                            x86_64  2.28-151.el8                              baseos     3.6 M
 glibc-common                     x86_64  2.28-151.el8                              baseos     1.3 M
 glibc-langpack-en                x86_64  2.28-151.el8                              baseos     825 k
 gmp                              x86_64  1:6.1.2-10.el8                            baseos     317 k
 gnupg2                           x86_64  2.2.20-2.el8                              baseos     2.4 M
 gnupg2-smime                     x86_64  2.2.20-2.el8                              baseos     282 k
 gnutls                           x86_64  3.6.14-8.el8_3                            baseos     1.0 M
 gobject-introspection            x86_64  1.56.1-1.el8                              baseos     254 k
 gpgme                            x86_64  1.13.1-7.el8                              baseos     335 k
 gpm-libs                         x86_64  1.20.7-17.el8                             appstream   38 k
 grep                             x86_64  3.1-6.el8                                 baseos     272 k
 groff-base                       x86_64  1.22.3-18.el8                             baseos     1.0 M
 grub2-common                     noarch  1:2.02-99.el8                             baseos     889 k
 grub2-pc                         x86_64  1:2.02-99.el8                             baseos      40 k
 grub2-pc-modules                 noarch  1:2.02-99.el8                             baseos     913 k
 grub2-tools                      x86_64  1:2.02-99.el8                             baseos     2.0 M
 grub2-tools-extra                x86_64  1:2.02-99.el8                             baseos     1.1 M
 grub2-tools-minimal              x86_64  1:2.02-99.el8                             baseos     208 k
 grubby                           x86_64  8.40-41.el8                               baseos      48 k
 gsettings-desktop-schemas        x86_64  3.32.0-5.el8                              baseos     632 k
 gzip                             x86_64  1.9-12.el8                                baseos     166 k
 hardlink                         x86_64  1:1.3-6.el8                               baseos      28 k
 hdparm                           x86_64  9.54-3.el8                                baseos      99 k
 hostname                         x86_64  3.20-6.el8                                baseos      31 k
 hwdata                           noarch  0.314-8.8.el8                             baseos     1.7 M
 ima-evm-utils                    x86_64  1.3.2-12.el8                              baseos      63 k
 info                             x86_64  6.5-6.el8                                 baseos     197 k
 initscripts                      x86_64  10.00.15-1.el8                            baseos     338 k
 ipcalc                           x86_64  0.2.4-4.el8                               baseos      37 k
 iproute                          x86_64  5.9.0-4.el8                               baseos     692 k
 iprutils                         x86_64  2.4.19-1.el8                              baseos     254 k
 ipset                            x86_64  7.1-1.el8                                 baseos      44 k
 ipset-libs                       x86_64  7.1-1.el8                                 baseos      70 k
 iptables                         x86_64  1.8.4-17.el8                              baseos     582 k
 iptables-ebtables                x86_64  1.8.4-17.el8                              baseos      70 k
 iptables-libs                    x86_64  1.8.4-17.el8                              baseos     106 k
 iptstate                         x86_64  2.2.6-6.el8                               baseos      53 k
 iputils                          x86_64  20180629-7.el8                            baseos     147 k
 irqbalance                       x86_64  2:1.4.0-6.el8                             baseos      55 k
 iscsi-initiator-utils            x86_64  6.2.1.2-1.gita8fcb37.el8                  baseos     378 k
 iscsi-initiator-utils-iscsiuio   x86_64  6.2.1.2-1.gita8fcb37.el8                  baseos      99 k
 isns-utils-libs                  x86_64  0.99-1.el8                                baseos     103 k
 iwl100-firmware                  noarch  39.31.5.1-102.el8.1                       baseos     170 k
 iwl1000-firmware                 noarch  1:39.31.5.1-102.el8.1                     baseos     233 k
 iwl105-firmware                  noarch  18.168.6.1-102.el8.1                      baseos     254 k
 iwl135-firmware                  noarch  18.168.6.1-102.el8.1                      baseos     263 k
 iwl2000-firmware                 noarch  18.168.6.1-102.el8.1                      baseos     257 k
 iwl2030-firmware                 noarch  18.168.6.1-102.el8.1                      baseos     265 k
 iwl3160-firmware                 noarch  1:25.30.13.0-102.el8.1                    baseos     1.7 M
 iwl5000-firmware                 noarch  8.83.5.1_1-102.el8.1                      baseos     314 k
 iwl5150-firmware                 noarch  8.24.2.2-102.el8.1                        baseos     166 k
 iwl6000-firmware                 noarch  9.221.4.1-102.el8.1                       baseos     187 k
 iwl6000g2a-firmware              noarch  18.168.6.1-102.el8.1                      baseos     329 k
 iwl6000g2b-firmware              noarch  18.168.6.1-102.el8.1                      baseos     330 k
 iwl6050-firmware                 noarch  41.28.5.1-102.el8.1                       baseos     262 k
 iwl7260-firmware                 noarch  1:25.30.13.0-102.el8.1                    baseos      16 M
 jansson                          x86_64  2.11-3.el8                                baseos      45 k
 jose                             x86_64  10-2.el8                                  appstream   56 k
 jq                               x86_64  1.5-12.el8                                appstream  160 k
 json-c                           x86_64  0.13.1-0.4.el8                            baseos      39 k
 json-glib                        x86_64  1.4.4-1.el8                               baseos     143 k
 kbd                              x86_64  2.0.4-10.el8                              baseos     389 k
 kbd-legacy                       noarch  2.0.4-10.el8                              baseos     480 k
 kbd-misc                         noarch  2.0.4-10.el8                              baseos     1.5 M
 kexec-tools                      x86_64  2.0.20-46.el8                             baseos     506 k
 keyutils-libs                    x86_64  1.5.10-6.el8                              baseos      33 k
 kmod                             x86_64  25-17.el8                                 baseos     125 k
 kmod-kvdo                        x86_64  6.2.4.26-77.el8                           baseos     336 k
 kmod-libs                        x86_64  25-17.el8                                 baseos      67 k
 kpartx                           x86_64  0.8.4-10.el8                              baseos     110 k
 kpatch                           noarch  0.9.2-3.el8                               baseos      15 k
 kpatch-dnf                       noarch  0.2-3.el8                                 baseos      16 k
 krb5-libs                        x86_64  1.18.2-8.el8                              baseos     837 k
 langpacks-en                     noarch  1.0-12.el8                                appstream  8.4 k
 ledmon                           x86_64  0.95-1.el8                                baseos      83 k
 less                             x86_64  530-1.el8                                 baseos     163 k
 libX11                           x86_64  1.6.8-4.el8                               appstream  610 k
 libX11-common                    noarch  1.6.8-4.el8                               appstream  157 k
 libXau                           x86_64  1.0.9-3.el8                               appstream   36 k
 libXext                          x86_64  1.3.4-1.el8                               appstream   44 k
 libXrender                       x86_64  0.9.10-7.el8                              appstream   32 k
 libaio                           x86_64  0.3.112-1.el8                             baseos      31 k
 libappstream-glib                x86_64  0.7.14-3.el8                              baseos     336 k
 libarchive                       x86_64  3.3.3-1.el8                               baseos     358 k
 libassuan                        x86_64  2.5.1-3.el8                               baseos      81 k
 libatasmart                      x86_64  0.19-14.el8                               appstream   49 k
 libattr                          x86_64  2.4.48-3.el8                              baseos      26 k
 libbasicobjects                  x86_64  0.1.1-39.el8                              baseos      30 k
 libblkid                         x86_64  2.32.1-27.el8                             baseos     216 k
 libblockdev                      x86_64  2.24-5.el8                                appstream  130 k
 libblockdev-crypto               x86_64  2.24-5.el8                                appstream   80 k
 libblockdev-fs                   x86_64  2.24-5.el8                                appstream   85 k
 libblockdev-loop                 x86_64  2.24-5.el8                                appstream   69 k
 libblockdev-lvm                  x86_64  2.24-5.el8                                appstream   85 k
 libblockdev-mdraid               x86_64  2.24-5.el8                                appstream   75 k
 libblockdev-part                 x86_64  2.24-5.el8                                appstream   78 k
 libblockdev-swap                 x86_64  2.24-5.el8                                appstream   71 k
 libblockdev-utils                x86_64  2.24-5.el8                                appstream   78 k
 libbytesize                      x86_64  1.4-3.el8                                 appstream   57 k
 libcap                           x86_64  2.26-4.el8                                baseos      59 k
 libcap-ng                        x86_64  0.7.9-5.el8                               baseos      32 k
 libcollection                    x86_64  0.7.0-39.el8                              baseos      47 k
 libcomps                         x86_64  0.1.11-5.el8                              baseos      80 k
 libconfig                        x86_64  1.5-9.el8                                 baseos      68 k
 libcroco                         x86_64  0.6.12-4.el8_2.1                          baseos     112 k
 libcurl                          x86_64  7.61.1-18.el8                             baseos     298 k
 libdaemon                        x86_64  0.14-15.el8                               baseos      35 k
 libdb                            x86_64  5.3.28-40.el8                             baseos     750 k
 libdb-utils                      x86_64  5.3.28-40.el8                             baseos     148 k
 libdhash                         x86_64  0.5.0-39.el8                              baseos      33 k
 libdnf                           x86_64  0.55.0-7.el8                              baseos     680 k
 libedit                          x86_64  3.1-23.20170329cvs.el8                    baseos     102 k
 libertas-usb8388-firmware        noarch  2:20201218-102.git05789708.el8            baseos     133 k
 libestr                          x86_64  0.1.10-1.el8                              appstream   26 k
 libevent                         x86_64  2.1.8-5.el8                               baseos     252 k
 libfastjson                      x86_64  0.99.8-2.el8                              appstream   36 k
 libfdisk                         x86_64  2.32.1-27.el8                             baseos     249 k
 libffi                           x86_64  3.1-22.el8                                baseos      36 k
 libfprint                        x86_64  1.90.7-1.el8                              appstream  252 k
 libgcc                           x86_64  8.4.1-1.el8                               baseos      77 k
 libgcrypt                        x86_64  1.8.5-4.el8                               baseos     461 k
 libgomp                          x86_64  8.4.1-1.el8                               baseos     203 k
 libgpg-error                     x86_64  1.31-1.el8                                baseos     240 k
 libgudev                         x86_64  232-4.el8                                 baseos      32 k
 libgusb                          x86_64  0.3.0-1.el8                               baseos      48 k
 libibverbs                       x86_64  32.0-4.el8                                baseos     320 k
 libicu                           x86_64  60.3-2.el8_1                              baseos     8.8 M
 libidn2                          x86_64  2.2.0-1.el8                               baseos      92 k
 libini_config                    x86_64  1.3.1-39.el8                              baseos      69 k
 libipa_hbac                      x86_64  2.4.0-9.el8                               baseos     109 k
 libjose                          x86_64  10-2.el8                                  appstream   62 k
 libkcapi                         x86_64  1.2.0-2.el8                               baseos      47 k
 libkcapi-hmaccalc                x86_64  1.2.0-2.el8                               baseos      30 k
 libksba                          x86_64  1.3.5-7.el8                               baseos     133 k
 libldb                           x86_64  2.2.0-2.el8                               baseos     187 k
 libluksmeta                      x86_64  9-4.el8                                   appstream   26 k
 libmaxminddb                     x86_64  1.2.0-10.el8                              appstream   32 k
 libmetalink                      x86_64  0.1.3-7.el8                               baseos      31 k
 libmnl                           x86_64  1.0.4-6.el8                               baseos      29 k
 libmodman                        x86_64  2.0.1-17.el8                              baseos      35 k
 libmodulemd                      x86_64  2.9.4-2.el8                               baseos     188 k
 libmount                         x86_64  2.32.1-27.el8                             baseos     232 k
 libndp                           x86_64  1.7-5.el8                                 baseos      39 k
 libnet                           x86_64  1.1.6-15.el8                              appstream   66 k
 libnetfilter_conntrack           x86_64  1.0.6-5.el8                               baseos      63 k
 libnfnetlink                     x86_64  1.0.1-13.el8                              baseos      32 k
 libnfsidmap                      x86_64  1:2.3.3-41.el8                            baseos     119 k
 libnftnl                         x86_64  1.1.5-4.el8                               baseos      82 k
 libnl3                           x86_64  3.5.0-1.el8                               baseos     319 k
 libnl3-cli                       x86_64  3.5.0-1.el8                               baseos     193 k
 libnsl2                          x86_64  1.2.0-2.20180605git4a062cf.el8            baseos      56 k
 libpath_utils                    x86_64  0.2.1-39.el8                              baseos      33 k
 libpcap                          x86_64  14:1.9.1-5.el8                            baseos     168 k
 libpipeline                      x86_64  1.5.0-2.el8                               baseos      53 k
 libpkgconf                       x86_64  1.4.2-1.el8                               baseos      34 k
 libpng                           x86_64  2:1.6.34-5.el8                            baseos     125 k
 libproxy                         x86_64  0.4.15-5.2.el8                            baseos      73 k
 libpsl                           x86_64  0.20.2-6.el8                              baseos      60 k
 libpwquality                     x86_64  1.4.4-3.el8                               baseos     106 k
 libref_array                     x86_64  0.1.5-39.el8                              baseos      32 k
 librelp                          x86_64  1.2.16-1.el8                              appstream   68 k
 librepo                          x86_64  1.12.0-3.el8                              baseos      90 k
 libseccomp                       x86_64  2.5.1-1.el8                               baseos      70 k
 libsecret                        x86_64  0.18.6-1.el8                              baseos     162 k
 libselinux                       x86_64  2.9-5.el8                                 baseos     164 k
 libselinux-utils                 x86_64  2.9-5.el8                                 baseos     242 k
 libsemanage                      x86_64  2.9-6.el8                                 baseos     164 k
 libsepol                         x86_64  2.9-2.el8                                 baseos     338 k
 libsigsegv                       x86_64  2.11-5.el8                                baseos      29 k
 libsmartcols                     x86_64  2.32.1-27.el8                             baseos     175 k
 libsmbclient                     x86_64  4.13.3-3.el8                              baseos     145 k
 libsolv                          x86_64  0.7.16-2.el8                              baseos     361 k
 libsoup                          x86_64  2.62.3-2.el8                              baseos     423 k
 libssh                           x86_64  0.9.4-2.el8                               baseos     213 k
 libssh-config                    noarch  0.9.4-2.el8                               baseos      17 k
 libsss_autofs                    x86_64  2.4.0-9.el8                               baseos     112 k
 libsss_certmap                   x86_64  2.4.0-9.el8                               baseos     148 k
 libsss_idmap                     x86_64  2.4.0-9.el8                               baseos     114 k
 libsss_nss_idmap                 x86_64  2.4.0-9.el8                               baseos     121 k
 libsss_sudo                      x86_64  2.4.0-9.el8                               baseos     110 k
 libstdc++                        x86_64  8.4.1-1.el8                               baseos     450 k
 libstemmer                       x86_64  0-10.585svn.el8                           baseos      72 k
 libstoragemgmt                   x86_64  1.8.7-1.el8                               baseos     244 k
 libsysfs                         x86_64  2.1.0-24.el8                              baseos      52 k
 libtalloc                        x86_64  2.3.1-2.el8                               baseos      48 k
 libtasn1                         x86_64  4.13-3.el8                                baseos      75 k
 libtdb                           x86_64  1.4.3-1.el8                               baseos      58 k
 libteam                          x86_64  1.31-2.el8                                baseos      63 k
 libtevent                        x86_64  0.10.2-2.el8                              baseos      48 k
 libtirpc                         x86_64  1.1.4-4.el8                               baseos     111 k
 libudisks2                       x86_64  2.9.0-6.el8                               appstream  192 k
 libunistring                     x86_64  0.9.9-3.el8                               baseos     419 k
 libusbx                          x86_64  1.0.23-4.el8                              baseos      73 k
 libuser                          x86_64  0.62-23.el8                               baseos     413 k
 libutempter                      x86_64  1.1.6-14.el8                              baseos      31 k
 libuuid                          x86_64  2.32.1-27.el8                             baseos      94 k
 libverto                         x86_64  0.3.0-5.el8                               baseos      23 k
 libwbclient                      x86_64  4.13.3-3.el8                              baseos     118 k
 libxcb                           x86_64  1.13.1-1.el8                              appstream  228 k
 libxcrypt                        x86_64  4.1.1-4.el8                               baseos      71 k
 libxkbcommon                     x86_64  0.9.1-1.el8                               appstream  115 k
 libxml2                          x86_64  2.9.7-9.el8                               baseos     695 k
 libxslt                          x86_64  1.1.32-6.el8                              baseos     249 k
 libyaml                          x86_64  0.1.7-5.el8                               baseos      60 k
 libzstd                          x86_64  1.4.4-1.el8                               baseos     265 k
 linux-firmware                   noarch  20201218-102.git05789708.el8              baseos     123 M
 lmdb-libs                        x86_64  0.9.24-1.el8                              baseos      57 k
 logrotate                        x86_64  3.14.0-4.el8                              baseos      85 k
 lshw                             x86_64  B.02.19.2-5.el8                           baseos     340 k
 lsof                             x86_64  4.93.2-1.el8                              baseos     252 k
 lsscsi                           x86_64  0.32-2.el8                                baseos      70 k
 lua-libs                         x86_64  5.3.4-11.el8                              baseos     117 k
 luksmeta                         x86_64  9-4.el8                                   appstream   21 k
 lvm2                             x86_64  8:2.03.11-5.el8                           baseos     1.6 M
 lvm2-libs                        x86_64  8:2.03.11-5.el8                           baseos     1.1 M
 lz4-libs                         x86_64  1.8.3-2.el8                               baseos      65 k
 lzo                              x86_64  2.08-14.el8                               baseos      68 k
 mailcap                          noarch  2.1.48-3.el8                              baseos      38 k
 man-db                           x86_64  2.7.6.1-17.el8                            baseos     885 k
 man-pages                        x86_64  4.15-6.el8                                baseos     5.9 M
 man-pages-overrides              noarch  8.3.0.2-2.el8                             appstream   69 k
 mcelog                           x86_64  3:173-0.el8                               baseos      81 k
 mdadm                            x86_64  4.1-15.el8                                baseos     454 k
 memstrack                        x86_64  0.1.11-1.el8                              baseos      46 k
 microcode_ctl                    x86_64  4:20210216-1.20210525.1.el8_4             baseos     5.5 M
 mlocate                          x86_64  0.26-20.el8                               baseos     120 k
 mozjs60                          x86_64  60.9.0-4.el8                              baseos     6.6 M
 mpfr                             x86_64  3.1.6-1.el8                               baseos     219 k
 mtr                              x86_64  2:0.92-3.el8                              baseos      94 k
 nano                             x86_64  2.9.8-1.el8                               baseos     579 k
 net-tools                        x86_64  2.0-0.52.20160912git.el8                  baseos     321 k
 newt                             x86_64  0.52.20-11.el8                            baseos     120 k
 nftables                         x86_64  1:0.9.3-18.el8                            baseos     312 k
 nmap-ncat                        x86_64  2:7.70-5.el8                              appstream  235 k
 npth                             x86_64  1.5-4.el8                                 baseos      25 k
 nspr                             x86_64  4.25.0-2.el8_2                            appstream  141 k
 nss                              x86_64  3.53.1-17.el8_3                           appstream  722 k
 nss-softokn                      x86_64  3.53.1-17.el8_3                           appstream  483 k
 nss-softokn-freebl               x86_64  3.53.1-17.el8_3                           appstream  375 k
 nss-sysinit                      x86_64  3.53.1-17.el8_3                           appstream   71 k
 nss-util                         x86_64  3.53.1-17.el8_3                           appstream  135 k
 numactl-libs                     x86_64  2.0.12-11.el8                             baseos      35 k
 oddjob                           x86_64  0.34.7-1.el8                              appstream   79 k
 oddjob-mkhomedir                 x86_64  0.34.7-1.el8                              appstream   48 k
 oniguruma                        x86_64  6.8.2-2.el8                               appstream  186 k
 openldap                         x86_64  2.4.46-16.el8                             baseos     350 k
 openssh                          x86_64  8.0p1-6.el8_4.2                           baseos     520 k
 openssh-clients                  x86_64  8.0p1-6.el8_4.2                           baseos     666 k
 openssh-server                   x86_64  8.0p1-6.el8_4.2                           baseos     483 k
 openssl                          x86_64  1:1.1.1g-15.el8_3                         baseos     706 k
 openssl-libs                     x86_64  1:1.1.1g-15.el8_3                         baseos     1.5 M
 openssl-pkcs11                   x86_64  0.4.10-2.el8                              baseos      65 k
 os-prober                        x86_64  1.74-6.el8                                baseos      50 k
 p11-kit                          x86_64  0.23.22-1.el8                             baseos     323 k
 p11-kit-trust                    x86_64  0.23.22-1.el8                             baseos     136 k
 pam                              x86_64  1.3.1-14.el8                              baseos     737 k
 parted                           x86_64  3.2-38.el8                                baseos     554 k
 passwd                           x86_64  0.80-3.el8                                baseos     114 k
 pciutils                         x86_64  3.7.0-1.el8                               baseos     104 k
 pciutils-libs                    x86_64  3.7.0-1.el8                               baseos      53 k
 pcre                             x86_64  8.42-4.el8                                baseos     209 k
 pcre2                            x86_64  10.32-2.el8                               baseos     245 k
 pigz                             x86_64  2.4-4.el8                                 baseos      78 k
 pinentry                         x86_64  1.1.0-2.el8                               appstream   99 k
 pinfo                            x86_64  0.6.10-18.el8                             appstream  124 k
 pixman                           x86_64  0.38.4-1.el8                              appstream  256 k
 pkgconf                          x86_64  1.4.2-1.el8                               baseos      37 k
 pkgconf-m4                       noarch  1.4.2-1.el8                               baseos      16 k
 pkgconf-pkg-config               x86_64  1.4.2-1.el8                               baseos      14 k
 platform-python-setuptools       noarch  39.2.0-6.el8                              baseos     630 k
 plymouth                         x86_64  0.9.4-9.20200615git1e36e30.el8            appstream  126 k
 plymouth-core-libs               x86_64  0.9.4-9.20200615git1e36e30.el8            appstream  121 k
 plymouth-scripts                 x86_64  0.9.4-9.20200615git1e36e30.el8            appstream   42 k
 policycoreutils                  x86_64  2.9-14.el8                                baseos     372 k
 policycoreutils-python-utils     noarch  2.9-14.el8                                baseos     251 k
 polkit                           x86_64  0.115-11.el8_4.1                          baseos     153 k
 polkit-libs                      x86_64  0.115-11.el8_4.1                          baseos      75 k
 polkit-pkla-compat               x86_64  0.1-12.el8                                baseos      45 k
 popt                             x86_64  1.18-1.el8                                baseos      60 k
 prefixdevname                    x86_64  0.1.0-6.el8                               baseos     467 k
 procps-ng                        x86_64  3.3.15-6.el8                              baseos     328 k
 protobuf-c                       x86_64  1.3.0-6.el8                               appstream   36 k
 psacct                           x86_64  6.6.3-4.el8                               baseos     103 k
 psmisc                           x86_64  23.1-5.el8                                baseos     150 k
 publicsuffix-list-dafsa          noarch  20180723-1.el8                            baseos      55 k
 python3-bind                     noarch  32:9.11.26-4.el8_4                        appstream  148 k
 python3-cairo                    x86_64  1.16.3-6.el8                              appstream   89 k
 python3-configobj                noarch  5.0.6-11.el8                              baseos      67 k
 python3-dateutil                 noarch  1:2.6.1-6.el8                             baseos     250 k
 python3-dbus                     x86_64  1.2.4-15.el8                              baseos     133 k
 python3-decorator                noarch  4.2.1-2.el8                               baseos      26 k
 python3-dnf                      noarch  4.4.2-11.el8                              baseos     540 k
 python3-dnf-plugins-core         noarch  4.0.18-4.el8                              baseos     233 k
 python3-firewall                 noarch  0.8.2-6.el8                               baseos     392 k
 python3-gobject                  x86_64  3.28.3-2.el8                              appstream   25 k
 python3-gobject-base             x86_64  3.28.3-2.el8                              baseos     312 k
 python3-gpg                      x86_64  1.13.1-7.el8                              baseos     244 k
 python3-hawkey                   x86_64  0.55.0-7.el8                              baseos     113 k
 python3-html5lib                 noarch  1:0.999999999-6.el8                       appstream  213 k
 python3-libcomps                 x86_64  0.1.11-5.el8                              baseos      51 k
 python3-libdnf                   x86_64  0.55.0-7.el8                              baseos     768 k
 python3-libselinux               x86_64  2.9-5.el8                                 baseos     282 k
 python3-libsemanage              x86_64  2.9-6.el8                                 baseos     126 k
 python3-libstoragemgmt           noarch  1.8.7-1.el8                               baseos     171 k
 python3-libstoragemgmt-clibs     x86_64  1.8.7-1.el8                               baseos      26 k
 python3-libxml2                  x86_64  2.9.7-9.el8                               baseos     236 k
 python3-linux-procfs             noarch  0.6.3-1.el8                               baseos      42 k
 python3-lxml                     x86_64  4.2.3-2.el8                               appstream  1.5 M
 python3-nftables                 x86_64  1:0.9.3-18.el8                            baseos      26 k
 python3-pexpect                  noarch  4.3.1-3.el8                               appstream  137 k
 python3-ply                      noarch  3.9-9.el8                                 baseos     110 k
 python3-policycoreutils          noarch  2.9-14.el8                                baseos     2.2 M
 python3-psutil                   x86_64  5.4.3-10.el8                              appstream  372 k
 python3-ptyprocess               noarch  0.5.2-4.el8                               appstream   30 k
 python3-pydbus                   noarch  0.6.0-5.el8                               appstream   52 k
 python3-pyudev                   noarch  0.21.0-7.el8                              baseos      83 k
 python3-pyyaml                   x86_64  3.12-12.el8                               baseos     192 k
 python3-rpm                      x86_64  4.14.3-13.el8                             baseos     156 k
 python3-schedutils               x86_64  0.6-6.el8                                 baseos      28 k
 python3-setools                  x86_64  4.3.0-2.el8                               baseos     625 k
 python3-setuptools               noarch  39.2.0-6.el8                              baseos     162 k
 python3-setuptools-wheel         noarch  39.2.0-6.el8                              baseos     286 k
 python3-six                      noarch  1.11.0-8.el8                              baseos      37 k
 python3-slip                     noarch  0.6.4-11.el8                              baseos      37 k
 python3-slip-dbus                noarch  0.6.4-11.el8                              baseos      38 k
 python3-sssdconfig               noarch  2.4.0-9.el8                               baseos     136 k
 python3-syspurpose               x86_64  1.28.13-2.el8                             baseos     302 k
 python3-systemd                  x86_64  234-8.el8                                 appstream   80 k
 python3-tracer                   noarch  0.7.5-2.el8                               appstream  121 k
 python3-unbound                  x86_64  1.7.3-15.el8                              appstream  118 k
 python3-webencodings             noarch  0.5.1-6.el8                               appstream   26 k
 quota                            x86_64  1:4.04-12.el8                             baseos     212 k
 quota-nls                        noarch  1:4.04-12.el8                             baseos      94 k
 rdma-core                        x86_64  32.0-4.el8                                baseos      58 k
 readline                         x86_64  7.0-10.el8                                baseos     198 k
 realmd                           x86_64  0.16.3-22.el8                             baseos     236 k
 rootfiles                        noarch  8.1-22.el8                                baseos      12 k
 rpm                              x86_64  4.14.3-13.el8                             baseos     541 k
 rpm-build-libs                   x86_64  4.14.3-13.el8                             baseos     154 k
 rpm-libs                         x86_64  4.14.3-13.el8                             baseos     338 k
 rpm-plugin-selinux               x86_64  4.14.3-13.el8                             baseos      75 k
 rpm-plugin-systemd-inhibit       x86_64  4.14.3-13.el8                             baseos      76 k
 rsync                            x86_64  3.1.3-12.el8                              baseos     404 k
 samba-client-libs                x86_64  4.13.3-3.el8                              baseos     5.4 M
 samba-common                     noarch  4.13.3-3.el8                              baseos     217 k
 samba-common-libs                x86_64  4.13.3-3.el8                              baseos     171 k
 sed                              x86_64  4.5-2.el8                                 baseos     297 k
 selinux-policy                   noarch  3.14.3-67.el8                             baseos     627 k
 selinux-policy-targeted          noarch  3.14.3-67.el8                             baseos      15 M
 setroubleshoot-plugins           noarch  3.3.13-1.el8                              appstream  360 k
 setroubleshoot-server            x86_64  3.3.24-3.el8                              appstream  400 k
 setup                            noarch  2.12.2-6.el8                              baseos     180 k
 sg3_utils                        x86_64  1.44-5.el8                                baseos     917 k
 sg3_utils-libs                   x86_64  1.44-5.el8                                baseos      98 k
 shadow-utils                     x86_64  2:4.6-12.el8                              baseos     1.2 M
 shared-mime-info                 x86_64  1.9-3.el8                                 baseos     328 k
 slang                            x86_64  2.3.2-3.el8                               baseos     367 k
 smartmontools                    x86_64  1:7.1-1.el8                               baseos     543 k
 snappy                           x86_64  1.1.8-3.el8                               baseos      36 k
 sos                              noarch  4.0-11.el8                                baseos     687 k
 sqlite                           x86_64  3.26.0-13.el8                             baseos     666 k
 sqlite-libs                      x86_64  3.26.0-13.el8                             baseos     579 k
 squashfs-tools                   x86_64  4.3-20.el8                                baseos     164 k
 sscg                             x86_64  2.3.3-14.el8                              appstream   48 k
 sssd                             x86_64  2.4.0-9.el8                               baseos     100 k
 sssd-ad                          x86_64  2.4.0-9.el8                               baseos     271 k
 sssd-client                      x86_64  2.4.0-9.el8                               baseos     195 k
 sssd-common                      x86_64  2.4.0-9.el8                               baseos     1.6 M
 sssd-common-pac                  x86_64  2.4.0-9.el8                               baseos     175 k
 sssd-ipa                         x86_64  2.4.0-9.el8                               baseos     356 k
 sssd-kcm                         x86_64  2.4.0-9.el8                               baseos     234 k
 sssd-krb5                        x86_64  2.4.0-9.el8                               baseos     143 k
 sssd-krb5-common                 x86_64  2.4.0-9.el8                               baseos     184 k
 sssd-ldap                        x86_64  2.4.0-9.el8                               baseos     220 k
 sssd-nfs-idmap                   x86_64  2.4.0-9.el8                               baseos     109 k
 sssd-proxy                       x86_64  2.4.0-9.el8                               baseos     144 k
 strace                           x86_64  5.7-2.el8                                 baseos     1.1 M
 sudo                             x86_64  1.8.29-7.el8                              baseos     924 k
 symlinks                         x86_64  1.4-19.el8                                baseos      22 k
 systemd                          x86_64  239-45.el8                                baseos     3.6 M
 systemd-libs                     x86_64  239-45.el8                                baseos     1.1 M
 systemd-pam                      x86_64  239-45.el8                                baseos     468 k
 systemd-udev                     x86_64  239-45.el8                                baseos     1.4 M
 tar                              x86_64  2:1.30-5.el8                              baseos     837 k
 tcpdump                          x86_64  14:4.9.3-1.el8                            appstream  451 k
 teamd                            x86_64  1.31-2.el8                                baseos     129 k
 time                             x86_64  1.9-3.el8                                 baseos      53 k
 timedatex                        x86_64  0.5-3.el8                                 baseos      31 k
 tpm2-tools                       x86_64  4.1.1-2.el8                               baseos     1.0 M
 tpm2-tss                         x86_64  2.3.2-3.el8                               baseos     274 k
 tracer-common                    noarch  0.7.5-2.el8                               appstream   33 k
 tree                             x86_64  1.7.0-15.el8                              baseos      58 k
 trousers                         x86_64  0.3.15-1.el8                              baseos     151 k
 trousers-lib                     x86_64  0.3.15-1.el8                              baseos     166 k
 tuned                            noarch  2.15.0-2.el8                              baseos     302 k
 tzdata                           noarch  2021a-1.el8                               baseos     472 k
 udisks2                          x86_64  2.9.0-6.el8                               appstream  473 k
 udisks2-iscsi                    x86_64  2.9.0-6.el8                               appstream   29 k
 udisks2-lvm2                     x86_64  2.9.0-6.el8                               appstream   44 k
 unbound-libs                     x86_64  1.7.3-15.el8                              appstream  501 k
 unzip                            x86_64  6.0-44.el8                                baseos     194 k
 usb_modeswitch-data              noarch  20191128-1.el8                            baseos     108 k
 usbutils                         x86_64  010-3.el8                                 baseos     107 k
 userspace-rcu                    x86_64  0.10.1-4.el8                              baseos     100 k
 util-linux                       x86_64  2.32.1-27.el8                             baseos     2.5 M
 util-linux-user                  x86_64  2.32.1-27.el8                             baseos      98 k
 vdo                              x86_64  6.2.4.14-14.el8                           baseos     589 k
 vim-common                       x86_64  2:8.0.1763-15.el8                         appstream  6.3 M
 vim-enhanced                     x86_64  2:8.0.1763-15.el8                         appstream  1.4 M
 vim-filesystem                   noarch  2:8.0.1763-15.el8                         appstream   47 k
 vim-minimal                      x86_64  2:8.0.1763-15.el8                         baseos     572 k
 virt-what                        x86_64  1.18-6.el8                                baseos      34 k
 volume_key-libs                  x86_64  0.3.11-5.el8                              appstream  147 k
 wget                             x86_64  1.19.5-10.el8                             appstream  733 k
 which                            x86_64  2.21-12.el8                               baseos      48 k
 words                            noarch  3.0-28.el8                                baseos     1.4 M
 xdg-utils                        noarch  1.1.2-5.el8                               appstream   83 k
 xfsdump                          x86_64  3.1.8-2.el8                               baseos     331 k
 xfsprogs                         x86_64  5.0.0-8.el8                               baseos     1.1 M
 xkeyboard-config                 noarch  2.28-1.el8                                appstream  781 k
 yajl                             x86_64  2.1.0-10.el8                              appstream   40 k
 yum                              noarch  4.4.2-11.el8                              baseos     201 k
 zip                              x86_64  3.0-23.el8                                baseos     269 k
 zlib                             x86_64  1.2.11-17.el8                             baseos     101 k
Downgrading:
 buildah                          x86_64  1.19.7-2.module+el8.4.0+556+40122d08      appstream  7.4 M
 cockpit-podman                   noarch  29-2.module+el8.4.0+556+40122d08          appstream  1.1 M
 conmon                           x86_64  2:2.0.26-3.module+el8.4.0+556+40122d08    appstream   51 k
 container-selinux                noarch  2:2.162.0-1.module+el8.4.0+556+40122d08   appstream   51 k
 containernetworking-plugins      x86_64  0.9.1-1.module+el8.4.0+556+40122d08       appstream   20 M
 containers-common                x86_64  1:1.2.2-10.module+el8.4.0+556+40122d08    appstream   98 k
 criu                             x86_64  3.15-1.module+el8.4.0+556+40122d08        appstream  510 k
 crun                             x86_64  0.18-2.module+el8.4.0+556+40122d08        appstream  184 k
 dhcp-client                      x86_64  12:4.3.6-44.el8_4.1                       baseos     317 k
 dhcp-common                      noarch  12:4.3.6-44.el8_4.1                       baseos     206 k
 dhcp-libs                        x86_64  12:4.3.6-44.el8_4.1                       baseos     147 k
 fuse-overlayfs                   x86_64  1.4.0-3.module+el8.4.0+556+40122d08       appstream   71 k
 libslirp                         x86_64  4.3.1-1.module+el8.4.0+556+40122d08       appstream   68 k
 nvme-cli                         x86_64  1.12-3.el8                                baseos     364 k
 podman                           x86_64  3.0.1-7.module+el8.4.0+556+40122d08       appstream   12 M
 podman-catatonit                 x86_64  3.0.1-7.module+el8.4.0+556+40122d08       appstream  322 k
 runc                             x86_64  1.0.0-73.rc93.module+el8.4.0+556+40122d08 appstream  3.2 M
 slirp4netns                      x86_64  1.1.8-1.module+el8.4.0+556+40122d08       appstream   50 k

Transaction Summary
====================================================================================================
Install     3 Packages
Upgrade    31 Packages
Downgrade  18 Packages

Total download size: 540 M
Downloading Packages:
(1/602): conmon-2.0.26-3.module+el8.4.0+556+401 121 kB/s |  51 kB     00:00    
(2/602): container-selinux-2.162.0-1.module+el8 301 kB/s |  51 kB     00:00    
(3/602): cockpit-podman-29-2.module+el8.4.0+556 739 kB/s | 1.1 MB     00:01    
(4/602): containers-common-1.2.2-10.module+el8. 196 kB/s |  98 kB     00:00    
(5/602): criu-3.15-1.module+el8.4.0+556+40122d0 901 kB/s | 510 kB     00:00    
(6/602): crun-0.18-2.module+el8.4.0+556+40122d0 339 kB/s | 184 kB     00:00    
(7/602): fuse-overlayfs-1.4.0-3.module+el8.4.0+ 444 kB/s |  71 kB     00:00    
(8/602): libslirp-4.3.1-1.module+el8.4.0+556+40 397 kB/s |  68 kB     00:00    
(9/602): buildah-1.19.7-2.module+el8.4.0+556+40 875 kB/s | 7.4 MB     00:08    
(10/602): podman-catatonit-3.0.1-7.module+el8.4 1.0 MB/s | 322 kB     00:00    
(11/602): runc-1.0.0-73.rc93.module+el8.4.0+556 970 kB/s | 3.2 MB     00:03    
(12/602): slirp4netns-1.1.8-1.module+el8.4.0+55 432 kB/s |  50 kB     00:00    
(13/602): dhcp-client-4.3.6-44.el8_4.1.x86_64.r 456 kB/s | 317 kB     00:00    
(14/602): dhcp-common-4.3.6-44.el8_4.1.noarch.r 781 kB/s | 206 kB     00:00    
(15/602): dhcp-libs-4.3.6-44.el8_4.1.x86_64.rpm 1.1 MB/s | 147 kB     00:00    
(16/602): nvme-cli-1.12-3.el8.x86_64.rpm        1.3 MB/s | 364 kB     00:00    
(17/602): PackageKit-1.1.12-6.el8.x86_64.rpm    1.2 MB/s | 598 kB     00:00    
(18/602): PackageKit-glib-1.1.12-6.el8.x86_64.r 924 kB/s | 139 kB     00:00    
(19/602): abattis-cantarell-fonts-0.0.25-6.el8. 956 kB/s | 154 kB     00:00    
(20/602): authselect-compat-1.2.2-2.el8.x86_64. 245 kB/s |  36 kB     00:00    
(21/602): bind-libs-9.11.26-4.el8_4.x86_64.rpm  734 kB/s | 173 kB     00:00    
(22/602): bind-libs-lite-9.11.26-4.el8_4.x86_64 1.0 MB/s | 1.2 MB     00:01    
(23/602): bind-license-9.11.26-4.el8_4.noarch.r 365 kB/s | 101 kB     00:00    
(24/602): podman-3.0.1-7.module+el8.4.0+556+401 889 kB/s |  12 MB     00:13    
(25/602): bind-utils-9.11.26-4.el8_4.x86_64.rpm 815 kB/s | 450 kB     00:00    
(26/602): cairo-gobject-1.15.12-3.el8.x86_64.rp 165 kB/s |  32 kB     00:00    
(27/602): clevis-15-1.el8.x86_64.rpm            162 kB/s |  56 kB     00:00    
(28/602): clevis-luks-15-1.el8.x86_64.rpm       226 kB/s |  36 kB     00:00    
(29/602): cairo-1.15.12-3.el8.x86_64.rpm        887 kB/s | 717 kB     00:00    
(30/602): cockpit-packagekit-238.2-1.el8.noarch 1.2 MB/s | 648 kB     00:00    
(31/602): desktop-file-utils-0.23-8.el8.x86_64. 137 kB/s |  79 kB     00:00    
(32/602): cockpit-storaged-238.2-1.el8.noarch.r 573 kB/s | 639 kB     00:01    
(33/602): fprintd-1.90.9-2.el8.x86_64.rpm       599 kB/s | 153 kB     00:00    
(34/602): fprintd-pam-1.90.9-2.el8.x86_64.rpm   183 kB/s |  27 kB     00:00    
(35/602): fstrm-0.6.0-3.el8.1.x86_64.rpm        294 kB/s |  28 kB     00:00    
(36/602): geolite2-country-20180605-1.el8.noarc 1.2 MB/s | 1.0 MB     00:00    
(37/602): gpm-libs-1.20.7-17.el8.x86_64.rpm     201 kB/s |  38 kB     00:00    
(38/602): jose-10-2.el8.x86_64.rpm              304 kB/s |  56 kB     00:00    
(39/602): jq-1.5-12.el8.x86_64.rpm              730 kB/s | 160 kB     00:00    
(40/602): langpacks-en-1.0-12.el8.noarch.rpm     43 kB/s | 8.4 kB     00:00    
(41/602): libX11-1.6.8-4.el8.x86_64.rpm         843 kB/s | 610 kB     00:00    
(42/602): libX11-common-1.6.8-4.el8.noarch.rpm  499 kB/s | 157 kB     00:00    
(43/602): libXau-1.0.9-3.el8.x86_64.rpm         136 kB/s |  36 kB     00:00    
(44/602): libXext-1.3.4-1.el8.x86_64.rpm        181 kB/s |  44 kB     00:00    
(45/602): libXrender-0.9.10-7.el8.x86_64.rpm     92 kB/s |  32 kB     00:00    
(46/602): libatasmart-0.19-14.el8.x86_64.rpm    170 kB/s |  49 kB     00:00    
(47/602): libblockdev-2.24-5.el8.x86_64.rpm     467 kB/s | 130 kB     00:00    
(48/602): libblockdev-crypto-2.24-5.el8.x86_64. 309 kB/s |  80 kB     00:00    
(49/602): libblockdev-fs-2.24-5.el8.x86_64.rpm  208 kB/s |  85 kB     00:00    
(50/602): libblockdev-loop-2.24-5.el8.x86_64.rp 186 kB/s |  69 kB     00:00    
(51/602): libblockdev-lvm-2.24-5.el8.x86_64.rpm 246 kB/s |  85 kB     00:00    
(52/602): libblockdev-mdraid-2.24-5.el8.x86_64. 270 kB/s |  75 kB     00:00    
(53/602): libblockdev-part-2.24-5.el8.x86_64.rp 214 kB/s |  78 kB     00:00    
(54/602): libblockdev-swap-2.24-5.el8.x86_64.rp 226 kB/s |  71 kB     00:00    
(55/602): libblockdev-utils-2.24-5.el8.x86_64.r  74 kB/s |  78 kB     00:01    
(56/602): libbytesize-1.4-3.el8.x86_64.rpm      172 kB/s |  57 kB     00:00    
(57/602): libestr-0.1.10-1.el8.x86_64.rpm        70 kB/s |  26 kB     00:00    
(58/602): containernetworking-plugins-0.9.1-1.m 759 kB/s |  20 MB     00:27    
(59/602): libfastjson-0.99.8-2.el8.x86_64.rpm    96 kB/s |  36 kB     00:00    
(60/602): libjose-10-2.el8.x86_64.rpm           263 kB/s |  62 kB     00:00    
(61/602): libfprint-1.90.7-1.el8.x86_64.rpm     678 kB/s | 252 kB     00:00    
(62/602): libluksmeta-9-4.el8.x86_64.rpm        106 kB/s |  26 kB     00:00    
(63/602): libmaxminddb-1.2.0-10.el8.x86_64.rpm  181 kB/s |  32 kB     00:00    
(64/602): libnet-1.1.6-15.el8.x86_64.rpm        324 kB/s |  66 kB     00:00    
(65/602): librelp-1.2.16-1.el8.x86_64.rpm       331 kB/s |  68 kB     00:00    
(66/602): libudisks2-2.9.0-6.el8.x86_64.rpm     633 kB/s | 192 kB     00:00    
(67/602): libxkbcommon-0.9.1-1.el8.x86_64.rpm   384 kB/s | 115 kB     00:00    
(68/602): libxcb-1.13.1-1.el8.x86_64.rpm        320 kB/s | 228 kB     00:00    
(69/602): luksmeta-9-4.el8.x86_64.rpm            70 kB/s |  21 kB     00:00    
(70/602): man-pages-overrides-8.3.0.2-2.el8.noa 307 kB/s |  69 kB     00:00    
(71/602): nmap-ncat-7.70-5.el8.x86_64.rpm       730 kB/s | 235 kB     00:00    
(72/602): nspr-4.25.0-2.el8_2.x86_64.rpm        437 kB/s | 141 kB     00:00    
(73/602): nss-3.53.1-17.el8_3.x86_64.rpm        1.0 MB/s | 722 kB     00:00    
(74/602): nss-softokn-freebl-3.53.1-17.el8_3.x8 902 kB/s | 375 kB     00:00    
(75/602): nss-softokn-3.53.1-17.el8_3.x86_64.rp 422 kB/s | 483 kB     00:01    
(76/602): nss-sysinit-3.53.1-17.el8_3.x86_64.rp 241 kB/s |  71 kB     00:00    
(77/602): geolite2-city-20180605-1.el8.noarch.r 1.5 MB/s |  19 MB     00:12    
(78/602): nss-util-3.53.1-17.el8_3.x86_64.rpm   342 kB/s | 135 kB     00:00    
(79/602): oddjob-0.34.7-1.el8.x86_64.rpm        332 kB/s |  79 kB     00:00    
(80/602): oniguruma-6.8.2-2.el8.x86_64.rpm      632 kB/s | 186 kB     00:00    
(81/602): oddjob-mkhomedir-0.34.7-1.el8.x86_64. 158 kB/s |  48 kB     00:00    
(82/602): pinentry-1.1.0-2.el8.x86_64.rpm       318 kB/s |  99 kB     00:00    
(83/602): pinfo-0.6.10-18.el8.x86_64.rpm        921 kB/s | 124 kB     00:00    
(84/602): plymouth-core-libs-0.9.4-9.20200615gi 1.1 MB/s | 121 kB     00:00    
(85/602): plymouth-scripts-0.9.4-9.20200615git1 475 kB/s |  42 kB     00:00    
(86/602): protobuf-c-1.3.0-6.el8.x86_64.rpm     236 kB/s |  36 kB     00:00    
(87/602): pixman-0.38.4-1.el8.x86_64.rpm        451 kB/s | 256 kB     00:00    
(88/602): python3-bind-9.11.26-4.el8_4.noarch.r 992 kB/s | 148 kB     00:00    
(89/602): plymouth-0.9.4-9.20200615git1e36e30.e 188 kB/s | 126 kB     00:00    
(90/602): python3-cairo-1.16.3-6.el8.x86_64.rpm 599 kB/s |  89 kB     00:00    
(91/602): python3-html5lib-0.999999999-6.el8.no 347 kB/s | 213 kB     00:00    
(92/602): python3-gobject-3.28.3-2.el8.x86_64.r  36 kB/s |  25 kB     00:00    
(93/602): python3-pexpect-4.3.1-3.el8.noarch.rp 534 kB/s | 137 kB     00:00    
(94/602): python3-lxml-4.2.3-2.el8.x86_64.rpm   1.1 MB/s | 1.5 MB     00:01    
(95/602): python3-psutil-5.4.3-10.el8.x86_64.rp 490 kB/s | 372 kB     00:00    
(96/602): python3-ptyprocess-0.5.2-4.el8.noarch  50 kB/s |  30 kB     00:00    
(97/602): python3-systemd-234-8.el8.x86_64.rpm  547 kB/s |  80 kB     00:00    
(98/602): python3-pydbus-0.6.0-5.el8.noarch.rpm 309 kB/s |  52 kB     00:00    
(99/602): python3-tracer-0.7.5-2.el8.noarch.rpm 481 kB/s | 121 kB     00:00    
(100/602): python3-webencodings-0.5.1-6.el8.noa 105 kB/s |  26 kB     00:00    
(101/602): python3-unbound-1.7.3-15.el8.x86_64. 443 kB/s | 118 kB     00:00    
(102/602): sscg-2.3.3-14.el8.x86_64.rpm         326 kB/s |  48 kB     00:00    
(103/602): setroubleshoot-server-3.3.24-3.el8.x 950 kB/s | 400 kB     00:00    
(104/602): tcpdump-4.9.3-1.el8.x86_64.rpm       1.4 MB/s | 451 kB     00:00    
(105/602): tracer-common-0.7.5-2.el8.noarch.rpm 279 kB/s |  33 kB     00:00    
(106/602): udisks2-iscsi-2.9.0-6.el8.x86_64.rpm 178 kB/s |  29 kB     00:00    
(107/602): udisks2-2.9.0-6.el8.x86_64.rpm       1.9 MB/s | 473 kB     00:00    
(108/602): udisks2-lvm2-2.9.0-6.el8.x86_64.rpm  401 kB/s |  44 kB     00:00    
(109/602): unbound-libs-1.7.3-15.el8.x86_64.rpm 1.9 MB/s | 501 kB     00:00    
(110/602): setroubleshoot-plugins-3.3.13-1.el8. 320 kB/s | 360 kB     00:01    
(111/602): vim-filesystem-8.0.1763-15.el8.noarc 180 kB/s |  47 kB     00:00    
(112/602): volume_key-libs-0.3.11-5.el8.x86_64. 382 kB/s | 147 kB     00:00    
(113/602): vim-enhanced-8.0.1763-15.el8.x86_64. 1.4 MB/s | 1.4 MB     00:00    
(114/602): xdg-utils-1.1.2-5.el8.noarch.rpm     356 kB/s |  83 kB     00:00    
(115/602): wget-1.19.5-10.el8.x86_64.rpm        737 kB/s | 733 kB     00:00    
(116/602): xkeyboard-config-2.28-1.el8.noarch.r 1.1 MB/s | 781 kB     00:00    
(117/602): yajl-2.1.0-10.el8.x86_64.rpm         148 kB/s |  40 kB     00:00    
(118/602): NetworkManager-config-server-1.30.0- 411 kB/s | 127 kB     00:00    
(119/602): NetworkManager-libnm-1.30.0-7.el8.x8 757 kB/s | 1.8 MB     00:02    
(120/602): NetworkManager-1.30.0-7.el8.x86_64.r 852 kB/s | 2.6 MB     00:03    
(121/602): vim-common-8.0.1763-15.el8.x86_64.rp 1.2 MB/s | 6.3 MB     00:05    
(122/602): NetworkManager-tui-1.30.0-7.el8.x86_ 1.6 MB/s | 326 kB     00:00    
(123/602): adcli-0.8.2-9.el8.x86_64.rpm         739 kB/s | 113 kB     00:00    
(124/602): at-3.1.20-11.el8.x86_64.rpm          168 kB/s |  80 kB     00:00    
(125/602): alsa-sof-firmware-1.6.1-2.el8.noarch 1.0 MB/s | 674 kB     00:00    
(126/602): NetworkManager-team-1.30.0-7.el8.x86 124 kB/s | 144 kB     00:01    
(127/602): attr-2.4.48-3.el8.x86_64.rpm         647 kB/s |  67 kB     00:00    
(128/602): authselect-1.2.2-2.el8.x86_64.rpm    1.0 MB/s | 132 kB     00:00    
(129/602): avahi-libs-0.7-20.el8.x86_64.rpm     307 kB/s |  61 kB     00:00    
(130/602): basesystem-11-5.el8.noarch.rpm        74 kB/s | 9.3 kB     00:00    
(131/602): authselect-libs-1.2.2-2.el8.x86_64.r 840 kB/s | 221 kB     00:00    
(132/602): bc-1.07.1-5.el8.x86_64.rpm           189 kB/s | 128 kB     00:00    
(133/602): bash-completion-2.7-5.el8.noarch.rpm 374 kB/s | 272 kB     00:00    
(134/602): bash-4.4.20-1.el8_4.x86_64.rpm       827 kB/s | 1.5 MB     00:01    
(135/602): biosdevname-0.7.3-2.el8.x86_64.rpm   156 kB/s |  43 kB     00:00    
(136/602): bind-export-libs-9.11.26-4.el8_4.x86 683 kB/s | 1.1 MB     00:01    
(137/602): blktrace-1.2.0-10.el8.x86_64.rpm     484 kB/s | 148 kB     00:00    
(138/602): bolt-0.9.1-1.el8.x86_64.rpm          643 kB/s | 200 kB     00:00    
(139/602): brotli-1.0.6-3.el8.x86_64.rpm        496 kB/s | 322 kB     00:00    
(140/602): bzip2-1.0.6-26.el8.x86_64.rpm        123 kB/s |  59 kB     00:00    
(141/602): bzip2-libs-1.0.6-26.el8.x86_64.rpm   196 kB/s |  47 kB     00:00    
(142/602): c-ares-1.13.0-5.el8.x86_64.rpm       366 kB/s |  92 kB     00:00    
(143/602): binutils-2.30-93.el8.x86_64.rpm      1.8 MB/s | 5.8 MB     00:03    
(144/602): checkpolicy-2.9-1.el8.x86_64.rpm     759 kB/s | 345 kB     00:00    
(145/602): chkconfig-1.13-2.el8.x86_64.rpm      616 kB/s | 193 kB     00:00    
(146/602): ca-certificates-2020.2.41-80.0.el8_2 419 kB/s | 390 kB     00:00    
(147/602): chrony-3.5-2.el8.x86_64.rpm          623 kB/s | 269 kB     00:00    
(148/602): cockpit-238.2-1.el8.x86_64.rpm       495 kB/s |  75 kB     00:00    
(149/602): cockpit-bridge-238.2-1.el8.x86_64.rp 958 kB/s | 534 kB     00:00    
(150/602): cockpit-ws-238.2-1.el8.x86_64.rpm    911 kB/s | 1.3 MB     00:01    
(151/602): coreutils-8.30-8.el8.x86_64.rpm      724 kB/s | 1.2 MB     00:01    
(152/602): cpio-2.12-10.el8.x86_64.rpm          263 kB/s | 264 kB     00:01    
(153/602): cracklib-2.9.6-15.el8.x86_64.rpm      69 kB/s |  92 kB     00:01    
(154/602): coreutils-common-8.30-8.el8.x86_64.r 609 kB/s | 2.0 MB     00:03    
(155/602): cronie-1.5.2-4.el8.x86_64.rpm         26 kB/s | 117 kB     00:04    
(156/602): cronie-anacron-1.5.2-4.el8.x86_64.rp 8.8 kB/s |  40 kB     00:04    
(157/602): cockpit-system-238.2-1.el8.noarch.rp 239 kB/s | 3.4 MB     00:14    
(158/602): crontabs-1.11-17.20190603git.el8.noa  38 kB/s |  24 kB     00:00    
(159/602): crypto-policies-20210209-1.gitbfb6be 186 kB/s |  61 kB     00:00    
(160/602): cryptsetup-2.3.3-4.el8.x86_64.rpm    917 kB/s | 189 kB     00:00    
(161/602): crypto-policies-scripts-20210209-1.g 135 kB/s |  66 kB     00:00    
(162/602): cracklib-dicts-2.9.6-15.el8.x86_64.r 367 kB/s | 4.0 MB     00:11    
(163/602): cryptsetup-libs-2.3.3-4.el8.x86_64.r 783 kB/s | 469 kB     00:00    
(164/602): cups-libs-2.2.6-38.el8.x86_64.rpm    668 kB/s | 432 kB     00:00    
(165/602): cyrus-sasl-gssapi-2.1.27-5.el8.x86_6 631 kB/s |  49 kB     00:00    
(166/602): cyrus-sasl-plain-2.1.27-5.el8.x86_64 501 kB/s |  46 kB     00:00    
(167/602): cyrus-sasl-lib-2.1.27-5.el8.x86_64.r 778 kB/s | 122 kB     00:00    
(168/602): dbus-1.12.8-12.el8_4.2.x86_64.rpm    463 kB/s |  40 kB     00:00    
(169/602): dbus-common-1.12.8-12.el8_4.2.noarch 558 kB/s |  45 kB     00:00    
(170/602): dbus-glib-0.110-2.el8.x86_64.rpm     686 kB/s | 126 kB     00:00    
(171/602): dbus-daemon-1.12.8-12.el8_4.2.x86_64 930 kB/s | 239 kB     00:00    
(172/602): dbus-libs-1.12.8-12.el8_4.2.x86_64.r 1.2 MB/s | 183 kB     00:00    
(173/602): dejavu-fonts-common-2.35-7.el8.noarc 790 kB/s |  73 kB     00:00    
(174/602): curl-7.61.1-18.el8.x86_64.rpm        393 kB/s | 352 kB     00:00    
(175/602): dbus-tools-1.12.8-12.el8_4.2.x86_64. 136 kB/s |  84 kB     00:00    
(176/602): dejavu-sans-mono-fonts-2.35-7.el8.no 971 kB/s | 446 kB     00:00    
(177/602): device-mapper-1.02.175-5.el8.x86_64. 905 kB/s | 374 kB     00:00    
(178/602): device-mapper-event-libs-1.02.175-5. 950 kB/s | 268 kB     00:00    
(179/602): device-mapper-event-1.02.175-5.el8.x 722 kB/s | 269 kB     00:00    
(180/602): device-mapper-libs-1.02.175-5.el8.x8 1.3 MB/s | 407 kB     00:00    
(181/602): device-mapper-multipath-0.8.4-10.el8 936 kB/s | 194 kB     00:00    
(182/602): device-mapper-multipath-libs-0.8.4-1 909 kB/s | 319 kB     00:00    
(183/602): device-mapper-persistent-data-0.8.5- 1.7 MB/s | 467 kB     00:00    
(184/602): diffutils-3.6-6.el8.x86_64.rpm       1.4 MB/s | 358 kB     00:00    
(185/602): dmidecode-3.2-8.el8.x86_64.rpm       766 kB/s |  90 kB     00:00    
(186/602): dnf-data-4.4.2-11.el8.noarch.rpm     1.1 MB/s | 150 kB     00:00    
(187/602): dnf-4.4.2-11.el8.noarch.rpm          1.7 MB/s | 538 kB     00:00    
(188/602): dosfstools-4.1-6.el8.x86_64.rpm      1.3 MB/s | 120 kB     00:00    
(189/602): dnf-plugins-core-4.0.18-4.el8.noarch 139 kB/s |  68 kB     00:00    
(190/602): dracut-049-135.git20210121.el8.x86_6 1.4 MB/s | 371 kB     00:00    
(191/602): dracut-config-rescue-049-135.git2021 624 kB/s |  57 kB     00:00    
(192/602): dracut-network-049-135.git20210121.e 855 kB/s | 104 kB     00:00    
(193/602): dracut-squash-049-135.git20210121.el 446 kB/s |  57 kB     00:00    
(194/602): ed-1.14.2-4.el8.x86_64.rpm           820 kB/s |  80 kB     00:00    
(195/602): elfutils-debuginfod-client-0.182-3.e 618 kB/s |  64 kB     00:00    
(196/602): dos2unix-7.4.0-3.el8.x86_64.rpm      305 kB/s | 240 kB     00:00    
(197/602): elfutils-default-yama-scope-0.182-3. 448 kB/s |  48 kB     00:00    
(198/602): emacs-filesystem-26.1-5.el8.noarch.r 344 kB/s |  68 kB     00:00    
(199/602): elfutils-libelf-0.182-3.el8.x86_64.r 675 kB/s | 215 kB     00:00    
(200/602): expat-2.2.5-4.el8.x86_64.rpm         349 kB/s | 110 kB     00:00    
(201/602): ethtool-5.8-5.el8.x86_64.rpm         558 kB/s | 205 kB     00:00    
(202/602): elfutils-libs-0.182-3.el8.x86_64.rpm 456 kB/s | 292 kB     00:00    
(203/602): file-5.33-16.el8_3.1.x86_64.rpm      576 kB/s |  76 kB     00:00    
(204/602): file-libs-5.33-16.el8_3.1.x86_64.rpm 1.2 MB/s | 542 kB     00:00    
(205/602): findutils-4.6.0-20.el8.x86_64.rpm    928 kB/s | 526 kB     00:00    
(206/602): firewalld-0.8.2-6.el8.noarch.rpm     1.6 MB/s | 487 kB     00:00    
(207/602): firewalld-filesystem-0.8.2-6.el8.noa 797 kB/s |  75 kB     00:00    
(208/602): fontpackages-filesystem-1.44-22.el8. 216 kB/s |  15 kB     00:00    
(209/602): filesystem-3.8-3.el8.x86_64.rpm      1.1 MB/s | 1.1 MB     00:00    
(210/602): fuse-common-3.2.1-12.el8.x86_64.rpm  203 kB/s |  20 kB     00:00    
(211/602): freetype-2.9.1-4.el8_3.1.x86_64.rpm  1.2 MB/s | 393 kB     00:00    
(212/602): fuse-libs-2.9.7-12.el8.x86_64.rpm    384 kB/s | 101 kB     00:00    
(213/602): fuse3-3.2.1-12.el8.x86_64.rpm        224 kB/s |  49 kB     00:00    
(214/602): fontconfig-2.13.1-3.el8.x86_64.rpm   353 kB/s | 273 kB     00:00    
(215/602): fuse3-libs-3.2.1-12.el8.x86_64.rpm   457 kB/s |  93 kB     00:00    
(216/602): gdbm-1.18-1.el8.x86_64.rpm           1.0 MB/s | 129 kB     00:00    
(217/602): gdbm-libs-1.18-1.el8.x86_64.rpm      524 kB/s |  59 kB     00:00    
(218/602): gdisk-1.0.3-6.el8.x86_64.rpm         1.4 MB/s | 237 kB     00:00    
(219/602): gdk-pixbuf2-2.36.12-5.el8.x86_64.rpm 1.1 MB/s | 465 kB     00:00    
(220/602): gawk-4.2.1-2.el8.x86_64.rpm          1.2 MB/s | 1.1 MB     00:00    
(221/602): gettext-0.19.8.1-17.el8.x86_64.rpm   1.6 MB/s | 1.1 MB     00:00    
(222/602): gettext-libs-0.19.8.1-17.el8.x86_64. 819 kB/s | 309 kB     00:00    
(223/602): glib-networking-2.56.1-1.1.el8.x86_6 870 kB/s | 153 kB     00:00    
(224/602): glibc-common-2.28-151.el8.x86_64.rpm 257 kB/s | 1.3 MB     00:05    
(225/602): glib2-2.56.4-10.el8_4.x86_64.rpm     453 kB/s | 2.5 MB     00:05    
(226/602): gmp-6.1.2-10.el8.x86_64.rpm          661 kB/s | 317 kB     00:00    
(227/602): glibc-langpack-en-2.28-151.el8.x86_6 674 kB/s | 825 kB     00:01    
(228/602): gnupg2-smime-2.2.20-2.el8.x86_64.rpm 415 kB/s | 282 kB     00:00    
(229/602): gnupg2-2.2.20-2.el8.x86_64.rpm       864 kB/s | 2.4 MB     00:02    
(230/602): gnutls-3.6.14-8.el8_3.x86_64.rpm     561 kB/s | 1.0 MB     00:01    
(231/602): gobject-introspection-1.56.1-1.el8.x 712 kB/s | 254 kB     00:00    
(232/602): glibc-2.28-151.el8.x86_64.rpm        391 kB/s | 3.6 MB     00:09    
(233/602): gpgme-1.13.1-7.el8.x86_64.rpm        615 kB/s | 335 kB     00:00    
(234/602): grep-3.1-6.el8.x86_64.rpm            1.0 MB/s | 272 kB     00:00    
(235/602): grub2-pc-2.02-99.el8.x86_64.rpm      234 kB/s |  40 kB     00:00    
(236/602): grub2-common-2.02-99.el8.noarch.rpm  787 kB/s | 889 kB     00:01    
(237/602): groff-base-1.22.3-18.el8.x86_64.rpm  697 kB/s | 1.0 MB     00:01    
(238/602): grub2-pc-modules-2.02-99.el8.noarch. 698 kB/s | 913 kB     00:01    
(239/602): grub2-tools-minimal-2.02-99.el8.x86_ 605 kB/s | 208 kB     00:00    
(240/602): grubby-8.40-41.el8.x86_64.rpm        320 kB/s |  48 kB     00:00    
(241/602): gsettings-desktop-schemas-3.32.0-5.e 462 kB/s | 632 kB     00:01    
(242/602): grub2-tools-extra-2.02-99.el8.x86_64 524 kB/s | 1.1 MB     00:02    
(243/602): gzip-1.9-12.el8.x86_64.rpm           694 kB/s | 166 kB     00:00    
(244/602): hardlink-1.3-6.el8.x86_64.rpm        263 kB/s |  28 kB     00:00    
(245/602): hdparm-9.54-3.el8.x86_64.rpm         743 kB/s |  99 kB     00:00    
(246/602): hostname-3.20-6.el8.x86_64.rpm       287 kB/s |  31 kB     00:00    
(247/602): ima-evm-utils-1.3.2-12.el8.x86_64.rp 325 kB/s |  63 kB     00:00    
(248/602): info-6.5-6.el8.x86_64.rpm            573 kB/s | 197 kB     00:00    
(249/602): initscripts-10.00.15-1.el8.x86_64.rp 517 kB/s | 338 kB     00:00    
(250/602): grub2-tools-2.02-99.el8.x86_64.rpm   515 kB/s | 2.0 MB     00:03    
(251/602): hwdata-0.314-8.8.el8.noarch.rpm      1.2 MB/s | 1.7 MB     00:01    
(252/602): ipcalc-0.2.4-4.el8.x86_64.rpm        239 kB/s |  37 kB     00:00    
(253/602): ipset-7.1-1.el8.x86_64.rpm           208 kB/s |  44 kB     00:00    
(254/602): iprutils-2.4.19-1.el8.x86_64.rpm     799 kB/s | 254 kB     00:00    
(255/602): ipset-libs-7.1-1.el8.x86_64.rpm      365 kB/s |  70 kB     00:00    
(256/602): iptables-ebtables-1.8.4-17.el8.x86_6 296 kB/s |  70 kB     00:00    
(257/602): iptables-1.8.4-17.el8.x86_64.rpm     880 kB/s | 582 kB     00:00    
(258/602): iptables-libs-1.8.4-17.el8.x86_64.rp 307 kB/s | 106 kB     00:00    
(259/602): iptstate-2.2.6-6.el8.x86_64.rpm      439 kB/s |  53 kB     00:00    
(260/602): iproute-5.9.0-4.el8.x86_64.rpm       584 kB/s | 692 kB     00:01    
(261/602): irqbalance-1.4.0-6.el8.x86_64.rpm    412 kB/s |  55 kB     00:00    
(262/602): iscsi-initiator-utils-iscsiuio-6.2.1 675 kB/s |  99 kB     00:00    
(263/602): isns-utils-libs-0.99-1.el8.x86_64.rp 453 kB/s | 103 kB     00:00    
(264/602): iputils-20180629-7.el8.x86_64.rpm    215 kB/s | 147 kB     00:00    
(265/602): iscsi-initiator-utils-6.2.1.2-1.gita 617 kB/s | 378 kB     00:00    
(266/602): iwl100-firmware-39.31.5.1-102.el8.1. 843 kB/s | 170 kB     00:00    
(267/602): iwl1000-firmware-39.31.5.1-102.el8.1 541 kB/s | 233 kB     00:00    
(268/602): iwl135-firmware-18.168.6.1-102.el8.1 635 kB/s | 263 kB     00:00    
(269/602): iwl105-firmware-18.168.6.1-102.el8.1 417 kB/s | 254 kB     00:00    
(270/602): iwl2000-firmware-18.168.6.1-102.el8. 618 kB/s | 257 kB     00:00    
(271/602): iwl2030-firmware-18.168.6.1-102.el8. 785 kB/s | 265 kB     00:00    
(272/602): iwl5000-firmware-8.83.5.1_1-102.el8. 731 kB/s | 314 kB     00:00    
(273/602): iwl5150-firmware-8.24.2.2-102.el8.1. 295 kB/s | 166 kB     00:00    
(274/602): iwl6000-firmware-9.221.4.1-102.el8.1 644 kB/s | 187 kB     00:00    
(275/602): iwl6000g2a-firmware-18.168.6.1-102.e 734 kB/s | 329 kB     00:00    
(276/602): iwl6000g2b-firmware-18.168.6.1-102.e 550 kB/s | 330 kB     00:00    
(277/602): iwl6050-firmware-41.28.5.1-102.el8.1 768 kB/s | 262 kB     00:00    
(278/602): jansson-2.11-3.el8.x86_64.rpm        147 kB/s |  45 kB     00:00    
(279/602): json-c-0.13.1-0.4.el8.x86_64.rpm     230 kB/s |  39 kB     00:00    
(280/602): json-glib-1.4.4-1.el8.x86_64.rpm     365 kB/s | 143 kB     00:00    
(281/602): iwl3160-firmware-25.30.13.0-102.el8. 652 kB/s | 1.7 MB     00:02    
(282/602): kbd-legacy-2.0.4-10.el8.noarch.rpm   335 kB/s | 480 kB     00:01    
(283/602): kbd-2.0.4-10.el8.x86_64.rpm          240 kB/s | 389 kB     00:01    
(284/602): kexec-tools-2.0.20-46.el8.x86_64.rpm 697 kB/s | 506 kB     00:00    
(285/602): keyutils-libs-1.5.10-6.el8.x86_64.rp 142 kB/s |  33 kB     00:00    
(286/602): kmod-25-17.el8.x86_64.rpm            609 kB/s | 125 kB     00:00    
(287/602): kmod-kvdo-6.2.4.26-77.el8.x86_64.rpm 770 kB/s | 336 kB     00:00    
(288/602): kmod-libs-25-17.el8.x86_64.rpm       396 kB/s |  67 kB     00:00    
(289/602): kbd-misc-2.0.4-10.el8.noarch.rpm     798 kB/s | 1.5 MB     00:01    
(290/602): kpartx-0.8.4-10.el8.x86_64.rpm       857 kB/s | 110 kB     00:00    
(291/602): kpatch-0.9.2-3.el8.noarch.rpm         98 kB/s |  15 kB     00:00    
(292/602): kpatch-dnf-0.2-3.el8.noarch.rpm      146 kB/s |  16 kB     00:00    
(293/602): ledmon-0.95-1.el8.x86_64.rpm         376 kB/s |  83 kB     00:00    
(294/602): less-530-1.el8.x86_64.rpm            790 kB/s | 163 kB     00:00    
(295/602): libaio-0.3.112-1.el8.x86_64.rpm      269 kB/s |  31 kB     00:00    
(296/602): krb5-libs-1.18.2-8.el8.x86_64.rpm    683 kB/s | 837 kB     00:01    
(297/602): libappstream-glib-0.7.14-3.el8.x86_6 308 kB/s | 336 kB     00:01    
(298/602): libassuan-2.5.1-3.el8.x86_64.rpm     371 kB/s |  81 kB     00:00    
(299/602): libarchive-3.3.3-1.el8.x86_64.rpm    507 kB/s | 358 kB     00:00    
(300/602): libattr-2.4.48-3.el8.x86_64.rpm      122 kB/s |  26 kB     00:00    
(301/602): libbasicobjects-0.1.1-39.el8.x86_64. 139 kB/s |  30 kB     00:00    
(302/602): libcap-2.26-4.el8.x86_64.rpm         311 kB/s |  59 kB     00:00    
(303/602): libblkid-2.32.1-27.el8.x86_64.rpm    644 kB/s | 216 kB     00:00    
(304/602): libcap-ng-0.7.9-5.el8.x86_64.rpm     232 kB/s |  32 kB     00:00    
(305/602): libcollection-0.7.0-39.el8.x86_64.rp 284 kB/s |  47 kB     00:00    
(306/602): libcomps-0.1.11-5.el8.x86_64.rpm     305 kB/s |  80 kB     00:00    
(307/602): libcroco-0.6.12-4.el8_2.1.x86_64.rpm 623 kB/s | 112 kB     00:00    
(308/602): libconfig-1.5-9.el8.x86_64.rpm       135 kB/s |  68 kB     00:00    
(309/602): libcurl-7.61.1-18.el8.x86_64.rpm     445 kB/s | 298 kB     00:00    
(310/602): libdaemon-0.14-15.el8.x86_64.rpm      34 kB/s |  35 kB     00:01    
(311/602): libdb-utils-5.3.28-40.el8.x86_64.rpm 116 kB/s | 148 kB     00:01    
(312/602): libdhash-0.5.0-39.el8.x86_64.rpm     139 kB/s |  33 kB     00:00    
(313/602): libdb-5.3.28-40.el8.x86_64.rpm       360 kB/s | 750 kB     00:02    
(314/602): libedit-3.1-23.20170329cvs.el8.x86_6 379 kB/s | 102 kB     00:00    
(315/602): libertas-usb8388-firmware-20201218-1 117 kB/s | 133 kB     00:01    
(316/602): libevent-2.1.8-5.el8.x86_64.rpm      522 kB/s | 252 kB     00:00    
(317/602): libfdisk-2.32.1-27.el8.x86_64.rpm    511 kB/s | 249 kB     00:00    
(318/602): libdnf-0.55.0-7.el8.x86_64.rpm       268 kB/s | 680 kB     00:02    
(319/602): libgcc-8.4.1-1.el8.x86_64.rpm        448 kB/s |  77 kB     00:00    
(320/602): libffi-3.1-22.el8.x86_64.rpm          79 kB/s |  36 kB     00:00    
(321/602): libgomp-8.4.1-1.el8.x86_64.rpm       666 kB/s | 203 kB     00:00    
(322/602): libgcrypt-1.8.5-4.el8.x86_64.rpm     648 kB/s | 461 kB     00:00    
(323/602): libgpg-error-1.31-1.el8.x86_64.rpm   874 kB/s | 240 kB     00:00    
(324/602): libgudev-232-4.el8.x86_64.rpm        327 kB/s |  32 kB     00:00    
(325/602): libgusb-0.3.0-1.el8.x86_64.rpm       444 kB/s |  48 kB     00:00    
(326/602): libibverbs-32.0-4.el8.x86_64.rpm     463 kB/s | 320 kB     00:00    
(327/602): libidn2-2.2.0-1.el8.x86_64.rpm       258 kB/s |  92 kB     00:00    
(328/602): libini_config-1.3.1-39.el8.x86_64.rp 247 kB/s |  69 kB     00:00    
(329/602): libipa_hbac-2.4.0-9.el8.x86_64.rpm   320 kB/s | 109 kB     00:00    
(330/602): libkcapi-1.2.0-2.el8.x86_64.rpm      238 kB/s |  47 kB     00:00    
(331/602): libkcapi-hmaccalc-1.2.0-2.el8.x86_64  97 kB/s |  30 kB     00:00    
(332/602): libksba-1.3.5-7.el8.x86_64.rpm        88 kB/s | 133 kB     00:01    
(333/602): libldb-2.2.0-2.el8.x86_64.rpm        255 kB/s | 187 kB     00:00    
(334/602): libmetalink-0.1.3-7.el8.x86_64.rpm   135 kB/s |  31 kB     00:00    
(335/602): libmnl-1.0.4-6.el8.x86_64.rpm        117 kB/s |  29 kB     00:00    
(336/602): libmodman-2.0.1-17.el8.x86_64.rpm    118 kB/s |  35 kB     00:00    
(337/602): iwl7260-firmware-25.30.13.0-102.el8. 845 kB/s |  16 MB     00:19    
(338/602): libmodulemd-2.9.4-2.el8.x86_64.rpm   233 kB/s | 188 kB     00:00    
(339/602): libndp-1.7-5.el8.x86_64.rpm          106 kB/s |  39 kB     00:00    
(340/602): libmount-2.32.1-27.el8.x86_64.rpm    377 kB/s | 232 kB     00:00    
(341/602): libnetfilter_conntrack-1.0.6-5.el8.x 212 kB/s |  63 kB     00:00    
(342/602): libnfnetlink-1.0.1-13.el8.x86_64.rpm 112 kB/s |  32 kB     00:00    
(343/602): libnfsidmap-2.3.3-41.el8.x86_64.rpm  220 kB/s | 119 kB     00:00    
(344/602): libicu-60.3-2.el8_1.x86_64.rpm       1.1 MB/s | 8.8 MB     00:07    
(345/602): libnftnl-1.1.5-4.el8.x86_64.rpm       89 kB/s |  82 kB     00:00    
(346/602): libnl3-cli-3.5.0-1.el8.x86_64.rpm    975 kB/s | 193 kB     00:00    
(347/602): libnl3-3.5.0-1.el8.x86_64.rpm        413 kB/s | 319 kB     00:00    
(348/602): libpath_utils-0.2.1-39.el8.x86_64.rp 346 kB/s |  33 kB     00:00    
(349/602): libpipeline-1.5.0-2.el8.x86_64.rpm   283 kB/s |  53 kB     00:00    
(350/602): libpcap-1.9.1-5.el8.x86_64.rpm       559 kB/s | 168 kB     00:00    
(351/602): libnsl2-1.2.0-2.20180605git4a062cf.e 105 kB/s |  56 kB     00:00    
(352/602): libpkgconf-1.4.2-1.el8.x86_64.rpm    406 kB/s |  34 kB     00:00    
(353/602): libproxy-0.4.15-5.2.el8.x86_64.rpm   662 kB/s |  73 kB     00:00    
(354/602): libpsl-0.20.2-6.el8.x86_64.rpm       498 kB/s |  60 kB     00:00    
(355/602): libpng-1.6.34-5.el8.x86_64.rpm       627 kB/s | 125 kB     00:00    
(356/602): libpwquality-1.4.4-3.el8.x86_64.rpm  798 kB/s | 106 kB     00:00    
(357/602): libref_array-0.1.5-39.el8.x86_64.rpm 315 kB/s |  32 kB     00:00    
(358/602): librepo-1.12.0-3.el8.x86_64.rpm      539 kB/s |  90 kB     00:00    
(359/602): libsecret-0.18.6-1.el8.x86_64.rpm    350 kB/s | 162 kB     00:00    
(360/602): libselinux-2.9-5.el8.x86_64.rpm      377 kB/s | 164 kB     00:00    
(361/602): libseccomp-2.5.1-1.el8.x86_64.rpm    122 kB/s |  70 kB     00:00    
(362/602): libselinux-utils-2.9-5.el8.x86_64.rp 1.1 MB/s | 242 kB     00:00    
(363/602): libsepol-2.9-2.el8.x86_64.rpm        959 kB/s | 338 kB     00:00    
(364/602): libsmartcols-2.32.1-27.el8.x86_64.rp 719 kB/s | 175 kB     00:00    
(365/602): libsigsegv-2.11-5.el8.x86_64.rpm      59 kB/s |  29 kB     00:00    
(366/602): libsemanage-2.9-6.el8.x86_64.rpm     207 kB/s | 164 kB     00:00    
(367/602): libsmbclient-4.13.3-3.el8.x86_64.rpm 905 kB/s | 145 kB     00:00    
(368/602): libssh-0.9.4-2.el8.x86_64.rpm        587 kB/s | 213 kB     00:00    
(369/602): libssh-config-0.9.4-2.el8.noarch.rpm 170 kB/s |  17 kB     00:00    
(370/602): libsss_autofs-2.4.0-9.el8.x86_64.rpm 424 kB/s | 112 kB     00:00    
(371/602): libsoup-2.62.3-2.el8.x86_64.rpm      527 kB/s | 423 kB     00:00    
(372/602): libsss_idmap-2.4.0-9.el8.x86_64.rpm  473 kB/s | 114 kB     00:00    
(373/602): libsss_certmap-2.4.0-9.el8.x86_64.rp 474 kB/s | 148 kB     00:00    
(374/602): libsss_sudo-2.4.0-9.el8.x86_64.rpm   275 kB/s | 110 kB     00:00    
(375/602): libsolv-0.7.16-2.el8.x86_64.rpm      215 kB/s | 361 kB     00:01    
(376/602): libsss_nss_idmap-2.4.0-9.el8.x86_64. 203 kB/s | 121 kB     00:00    
(377/602): libstemmer-0-10.585svn.el8.x86_64.rp 565 kB/s |  72 kB     00:00    
(378/602): libsysfs-2.1.0-24.el8.x86_64.rpm     538 kB/s |  52 kB     00:00    
(379/602): libtalloc-2.3.1-2.el8.x86_64.rpm     456 kB/s |  48 kB     00:00    
(380/602): libtasn1-4.13-3.el8.x86_64.rpm       598 kB/s |  75 kB     00:00    
(381/602): libstdc++-8.4.1-1.el8.x86_64.rpm     779 kB/s | 450 kB     00:00    
(382/602): libtdb-1.4.3-1.el8.x86_64.rpm        226 kB/s |  58 kB     00:00    
(383/602): libteam-1.31-2.el8.x86_64.rpm        254 kB/s |  63 kB     00:00    
(384/602): libtevent-0.10.2-2.el8.x86_64.rpm    345 kB/s |  48 kB     00:00    
(385/602): libstoragemgmt-1.8.7-1.el8.x86_64.rp 295 kB/s | 244 kB     00:00    
(386/602): libtirpc-1.1.4-4.el8.x86_64.rpm      536 kB/s | 111 kB     00:00    
(387/602): libunistring-0.9.9-3.el8.x86_64.rpm  880 kB/s | 419 kB     00:00    
(388/602): libutempter-1.1.6-14.el8.x86_64.rpm  375 kB/s |  31 kB     00:00    
(389/602): libuser-0.62-23.el8.x86_64.rpm       714 kB/s | 413 kB     00:00    
(390/602): libusbx-1.0.23-4.el8.x86_64.rpm      115 kB/s |  73 kB     00:00    
(391/602): libuuid-2.32.1-27.el8.x86_64.rpm     685 kB/s |  94 kB     00:00    
(392/602): libverto-0.3.0-5.el8.x86_64.rpm      264 kB/s |  23 kB     00:00    
(393/602): libxcrypt-4.1.1-4.el8.x86_64.rpm     660 kB/s |  71 kB     00:00    
(394/602): libwbclient-4.13.3-3.el8.x86_64.rpm  676 kB/s | 118 kB     00:00    
(395/602): libyaml-0.1.7-5.el8.x86_64.rpm       276 kB/s |  60 kB     00:00    
(396/602): libxslt-1.1.32-6.el8.x86_64.rpm      609 kB/s | 249 kB     00:00    
(397/602): libzstd-1.4.4-1.el8.x86_64.rpm       778 kB/s | 265 kB     00:00    
(398/602): lmdb-libs-0.9.24-1.el8.x86_64.rpm    385 kB/s |  57 kB     00:00    
(399/602): logrotate-3.14.0-4.el8.x86_64.rpm    480 kB/s |  85 kB     00:00    
(400/602): libxml2-2.9.7-9.el8.x86_64.rpm       499 kB/s | 695 kB     00:01    
(401/602): lshw-B.02.19.2-5.el8.x86_64.rpm      892 kB/s | 340 kB     00:00    
(402/602): lsscsi-0.32-2.el8.x86_64.rpm         189 kB/s |  70 kB     00:00    
(403/602): lua-libs-5.3.4-11.el8.x86_64.rpm     635 kB/s | 117 kB     00:00    
(404/602): lsof-4.93.2-1.el8.x86_64.rpm         390 kB/s | 252 kB     00:00    
(405/602): lvm2-2.03.11-5.el8.x86_64.rpm        876 kB/s | 1.6 MB     00:01    
(406/602): lz4-libs-1.8.3-2.el8.x86_64.rpm      326 kB/s |  65 kB     00:00    
(407/602): lzo-2.08-14.el8.x86_64.rpm           269 kB/s |  68 kB     00:00    
(408/602): mailcap-2.1.48-3.el8.noarch.rpm      204 kB/s |  38 kB     00:00    
(409/602): lvm2-libs-2.03.11-5.el8.x86_64.rpm   323 kB/s | 1.1 MB     00:03    
(410/602): man-db-2.7.6.1-17.el8.x86_64.rpm     703 kB/s | 885 kB     00:01    
(411/602): mcelog-173-0.el8.x86_64.rpm          171 kB/s |  81 kB     00:00    
(412/602): mdadm-4.1-15.el8.x86_64.rpm          1.1 MB/s | 454 kB     00:00    
(413/602): memstrack-0.1.11-1.el8.x86_64.rpm    364 kB/s |  46 kB     00:00    
(414/602): microcode_ctl-20210216-1.20210525.1. 1.1 MB/s | 5.5 MB     00:04    
(415/602): mlocate-0.26-20.el8.x86_64.rpm       262 kB/s | 120 kB     00:00    
(416/602): man-pages-4.15-6.el8.x86_64.rpm      334 kB/s | 5.9 MB     00:18    
(417/602): mpfr-3.1.6-1.el8.x86_64.rpm          448 kB/s | 219 kB     00:00    
(418/602): mtr-0.92-3.el8.x86_64.rpm            383 kB/s |  94 kB     00:00    
(419/602): nano-2.9.8-1.el8.x86_64.rpm          282 kB/s | 579 kB     00:02    
(420/602): net-tools-2.0-0.52.20160912git.el8.x 268 kB/s | 321 kB     00:01    
(421/602): newt-0.52.20-11.el8.x86_64.rpm       201 kB/s | 120 kB     00:00    
(422/602): nftables-0.9.3-18.el8.x86_64.rpm     290 kB/s | 312 kB     00:01    
(423/602): npth-1.5-4.el8.x86_64.rpm             69 kB/s |  25 kB     00:00    
(424/602): numactl-libs-2.0.12-11.el8.x86_64.rp  27 kB/s |  35 kB     00:01    
(425/602): openldap-2.4.46-16.el8.x86_64.rpm    100 kB/s | 350 kB     00:03    
(426/602): mozjs60-60.9.0-4.el8.x86_64.rpm      276 kB/s | 6.6 MB     00:24    
(427/602): openssh-8.0p1-6.el8_4.2.x86_64.rpm   101 kB/s | 520 kB     00:05    
(428/602): openssh-server-8.0p1-6.el8_4.2.x86_6 524 kB/s | 483 kB     00:00    
(429/602): openssh-clients-8.0p1-6.el8_4.2.x86_ 138 kB/s | 666 kB     00:04    
(430/602): openssl-1.1.1g-15.el8_3.x86_64.rpm   581 kB/s | 706 kB     00:01    
(431/602): openssl-pkcs11-0.4.10-2.el8.x86_64.r 448 kB/s |  65 kB     00:00    
(432/602): os-prober-1.74-6.el8.x86_64.rpm      336 kB/s |  50 kB     00:00    
(433/602): p11-kit-0.23.22-1.el8.x86_64.rpm     557 kB/s | 323 kB     00:00    
(434/602): p11-kit-trust-0.23.22-1.el8.x86_64.r 562 kB/s | 136 kB     00:00    
(435/602): pam-1.3.1-14.el8.x86_64.rpm          597 kB/s | 737 kB     00:01    
(436/602): openssl-libs-1.1.1g-15.el8_3.x86_64. 371 kB/s | 1.5 MB     00:04    
(437/602): parted-3.2-38.el8.x86_64.rpm         346 kB/s | 554 kB     00:01    
(438/602): passwd-0.80-3.el8.x86_64.rpm         185 kB/s | 114 kB     00:00    
(439/602): pciutils-3.7.0-1.el8.x86_64.rpm      360 kB/s | 104 kB     00:00    
(440/602): pciutils-libs-3.7.0-1.el8.x86_64.rpm 143 kB/s |  53 kB     00:00    
(441/602): pcre-8.42-4.el8.x86_64.rpm           499 kB/s | 209 kB     00:00    
(442/602): pigz-2.4-4.el8.x86_64.rpm            254 kB/s |  78 kB     00:00    
(443/602): pcre2-10.32-2.el8.x86_64.rpm         337 kB/s | 245 kB     00:00    
(444/602): pkgconf-1.4.2-1.el8.x86_64.rpm       213 kB/s |  37 kB     00:00    
(445/602): pkgconf-m4-1.4.2-1.el8.noarch.rpm     52 kB/s |  16 kB     00:00    
(446/602): pkgconf-pkg-config-1.4.2-1.el8.x86_6  62 kB/s |  14 kB     00:00    
(447/602): policycoreutils-2.9-14.el8.x86_64.rp 509 kB/s | 372 kB     00:00    
(448/602): policycoreutils-python-utils-2.9-14. 520 kB/s | 251 kB     00:00    
(449/602): polkit-0.115-11.el8_4.1.x86_64.rpm   258 kB/s | 153 kB     00:00    
(450/602): polkit-libs-0.115-11.el8_4.1.x86_64. 284 kB/s |  75 kB     00:00    
(451/602): platform-python-setuptools-39.2.0-6. 285 kB/s | 630 kB     00:02    
(452/602): polkit-pkla-compat-0.1-12.el8.x86_64 207 kB/s |  45 kB     00:00    
(453/602): popt-1.18-1.el8.x86_64.rpm           215 kB/s |  60 kB     00:00    
(454/602): prefixdevname-0.1.0-6.el8.x86_64.rpm 100 kB/s | 467 kB     00:04    
(455/602): psacct-6.6.3-4.el8.x86_64.rpm         94 kB/s | 103 kB     00:01    
(456/602): procps-ng-3.3.15-6.el8.x86_64.rpm     58 kB/s | 328 kB     00:05    
(457/602): publicsuffix-list-dafsa-20180723-1.e  89 kB/s |  55 kB     00:00    
(458/602): psmisc-23.1-5.el8.x86_64.rpm         117 kB/s | 150 kB     00:01    
(459/602): python3-configobj-5.0.6-11.el8.noarc 103 kB/s |  67 kB     00:00    
(460/602): python3-dbus-1.2.4-15.el8.x86_64.rpm  94 kB/s | 133 kB     00:01    
(461/602): python3-dateutil-2.6.1-6.el8.noarch. 108 kB/s | 250 kB     00:02    
(462/602): python3-decorator-4.2.1-2.el8.noarch  17 kB/s |  26 kB     00:01    
(463/602): python3-dnf-plugins-core-4.0.18-4.el  90 kB/s | 233 kB     00:02    
(464/602): python3-dnf-4.4.2-11.el8.noarch.rpm  141 kB/s | 540 kB     00:03    
(465/602): python3-firewall-0.8.2-6.el8.noarch. 289 kB/s | 392 kB     00:01    
(466/602): python3-gobject-base-3.28.3-2.el8.x8 334 kB/s | 312 kB     00:00    
(467/602): python3-hawkey-0.55.0-7.el8.x86_64.r 137 kB/s | 113 kB     00:00    
(468/602): python3-gpg-1.13.1-7.el8.x86_64.rpm  186 kB/s | 244 kB     00:01    
(469/602): python3-libcomps-0.1.11-5.el8.x86_64  54 kB/s |  51 kB     00:00    
(470/602): python3-libselinux-2.9-5.el8.x86_64. 390 kB/s | 282 kB     00:00    
(471/602): python3-libdnf-0.55.0-7.el8.x86_64.r 392 kB/s | 768 kB     00:01    
(472/602): python3-libsemanage-2.9-6.el8.x86_64 158 kB/s | 126 kB     00:00    
(473/602): python3-libstoragemgmt-clibs-1.8.7-1 170 kB/s |  26 kB     00:00    
(474/602): python3-libstoragemgmt-1.8.7-1.el8.n 652 kB/s | 171 kB     00:00    
(475/602): python3-linux-procfs-0.6.3-1.el8.noa 247 kB/s |  42 kB     00:00    
(476/602): python3-libxml2-2.9.7-9.el8.x86_64.r 646 kB/s | 236 kB     00:00    
(477/602): python3-nftables-0.9.3-18.el8.x86_64 166 kB/s |  26 kB     00:00    
(478/602): python3-ply-3.9-9.el8.noarch.rpm     462 kB/s | 110 kB     00:00    
(479/602): python3-pyudev-0.21.0-7.el8.noarch.r 391 kB/s |  83 kB     00:00    
(480/602): python3-pyyaml-3.12-12.el8.x86_64.rp 749 kB/s | 192 kB     00:00    
(481/602): python3-rpm-4.14.3-13.el8.x86_64.rpm 540 kB/s | 156 kB     00:00    
(482/602): python3-schedutils-0.6-6.el8.x86_64. 163 kB/s |  28 kB     00:00    
(483/602): python3-setools-4.3.0-2.el8.x86_64.r 513 kB/s | 625 kB     00:01    
(484/602): python3-setuptools-39.2.0-6.el8.noar 378 kB/s | 162 kB     00:00    
(485/602): python3-setuptools-wheel-39.2.0-6.el 358 kB/s | 286 kB     00:00    
(486/602): python3-policycoreutils-2.9-14.el8.n 598 kB/s | 2.2 MB     00:03    
(487/602): python3-six-1.11.0-8.el8.noarch.rpm  169 kB/s |  37 kB     00:00    
(488/602): python3-slip-0.6.4-11.el8.noarch.rpm 328 kB/s |  37 kB     00:00    
(489/602): python3-slip-dbus-0.6.4-11.el8.noarc 242 kB/s |  38 kB     00:00    
(490/602): python3-sssdconfig-2.4.0-9.el8.noarc 325 kB/s | 136 kB     00:00    
(491/602): quota-4.04-12.el8.x86_64.rpm         557 kB/s | 212 kB     00:00    
(492/602): python3-syspurpose-1.28.13-2.el8.x86 339 kB/s | 302 kB     00:00    
(493/602): quota-nls-4.04-12.el8.noarch.rpm     364 kB/s |  94 kB     00:00    
(494/602): rdma-core-32.0-4.el8.x86_64.rpm      272 kB/s |  58 kB     00:00    
(495/602): readline-7.0-10.el8.x86_64.rpm       920 kB/s | 198 kB     00:00    
(496/602): realmd-0.16.3-22.el8.x86_64.rpm      433 kB/s | 236 kB     00:00    
(497/602): rootfiles-8.1-22.el8.noarch.rpm       18 kB/s |  12 kB     00:00    
(498/602): rpm-build-libs-4.14.3-13.el8.x86_64. 401 kB/s | 154 kB     00:00    
(499/602): rpm-4.14.3-13.el8.x86_64.rpm         386 kB/s | 541 kB     00:01    
(500/602): rpm-libs-4.14.3-13.el8.x86_64.rpm    434 kB/s | 338 kB     00:00    
(501/602): rpm-plugin-selinux-4.14.3-13.el8.x86 381 kB/s |  75 kB     00:00    
(502/602): rpm-plugin-systemd-inhibit-4.14.3-13 316 kB/s |  76 kB     00:00    
(503/602): rsync-3.1.3-12.el8.x86_64.rpm        336 kB/s | 404 kB     00:01    
(504/602): samba-common-4.13.3-3.el8.noarch.rpm 277 kB/s | 217 kB     00:00    
(505/602): samba-common-libs-4.13.3-3.el8.x86_6 210 kB/s | 171 kB     00:00    
(506/602): sed-4.5-2.el8.x86_64.rpm              95 kB/s | 297 kB     00:03    
(507/602): samba-client-libs-4.13.3-3.el8.x86_6 720 kB/s | 5.4 MB     00:07    
(508/602): selinux-policy-3.14.3-67.el8.noarch. 160 kB/s | 627 kB     00:03    
(509/602): setup-2.12.2-6.el8.noarch.rpm        204 kB/s | 180 kB     00:00    
(510/602): sg3_utils-1.44-5.el8.x86_64.rpm      186 kB/s | 917 kB     00:04    
(511/602): sg3_utils-libs-1.44-5.el8.x86_64.rpm 128 kB/s |  98 kB     00:00    
(512/602): shadow-utils-4.6-12.el8.x86_64.rpm   191 kB/s | 1.2 MB     00:06    
(513/602): shared-mime-info-1.9-3.el8.x86_64.rp 298 kB/s | 328 kB     00:01    
(514/602): slang-2.3.2-3.el8.x86_64.rpm         250 kB/s | 367 kB     00:01    
(515/602): smartmontools-7.1-1.el8.x86_64.rpm   265 kB/s | 543 kB     00:02    
(516/602): snappy-1.1.8-3.el8.x86_64.rpm        141 kB/s |  36 kB     00:00    
(517/602): sos-4.0-11.el8.noarch.rpm            230 kB/s | 687 kB     00:02    
(518/602): sqlite-3.26.0-13.el8.x86_64.rpm      301 kB/s | 666 kB     00:02    
(519/602): sqlite-libs-3.26.0-13.el8.x86_64.rpm 199 kB/s | 579 kB     00:02    
(520/602): squashfs-tools-4.3-20.el8.x86_64.rpm 272 kB/s | 164 kB     00:00    
(521/602): sssd-2.4.0-9.el8.x86_64.rpm          311 kB/s | 100 kB     00:00    
(522/602): sssd-ad-2.4.0-9.el8.x86_64.rpm       174 kB/s | 271 kB     00:01    
(523/602): sssd-client-2.4.0-9.el8.x86_64.rpm   251 kB/s | 195 kB     00:00    
(524/602): selinux-policy-targeted-3.14.3-67.el 470 kB/s |  15 MB     00:32    
(525/602): sssd-common-pac-2.4.0-9.el8.x86_64.r 287 kB/s | 175 kB     00:00    
(526/602): sssd-common-2.4.0-9.el8.x86_64.rpm   596 kB/s | 1.6 MB     00:02    
(527/602): sssd-kcm-2.4.0-9.el8.x86_64.rpm      414 kB/s | 234 kB     00:00    
(528/602): sssd-krb5-2.4.0-9.el8.x86_64.rpm     230 kB/s | 143 kB     00:00    
(529/602): sssd-ipa-2.4.0-9.el8.x86_64.rpm      160 kB/s | 356 kB     00:02    
(530/602): sssd-krb5-common-2.4.0-9.el8.x86_64. 562 kB/s | 184 kB     00:00    
(531/602): sssd-nfs-idmap-2.4.0-9.el8.x86_64.rp 340 kB/s | 109 kB     00:00    
(532/602): sssd-ldap-2.4.0-9.el8.x86_64.rpm     349 kB/s | 220 kB     00:00    
(533/602): sssd-proxy-2.4.0-9.el8.x86_64.rpm    278 kB/s | 144 kB     00:00    
(534/602): sudo-1.8.29-7.el8.x86_64.rpm         715 kB/s | 924 kB     00:01    
(535/602): symlinks-1.4-19.el8.x86_64.rpm        65 kB/s |  22 kB     00:00    
(536/602): strace-5.7-2.el8.x86_64.rpm          343 kB/s | 1.1 MB     00:03    
(537/602): systemd-239-45.el8.x86_64.rpm        1.0 MB/s | 3.6 MB     00:03    
(538/602): systemd-pam-239-45.el8.x86_64.rpm    478 kB/s | 468 kB     00:00    
(539/602): systemd-libs-239-45.el8.x86_64.rpm   258 kB/s | 1.1 MB     00:04    
(540/602): systemd-udev-239-45.el8.x86_64.rpm   776 kB/s | 1.4 MB     00:01    
(541/602): teamd-1.31-2.el8.x86_64.rpm          272 kB/s | 129 kB     00:00    
(542/602): time-1.9-3.el8.x86_64.rpm            115 kB/s |  53 kB     00:00    
(543/602): timedatex-0.5-3.el8.x86_64.rpm        97 kB/s |  31 kB     00:00    
(544/602): tpm2-tools-4.1.1-2.el8.x86_64.rpm    897 kB/s | 1.0 MB     00:01    
(545/602): tpm2-tss-2.3.2-3.el8.x86_64.rpm      650 kB/s | 274 kB     00:00    
(546/602): tree-1.7.0-15.el8.x86_64.rpm         245 kB/s |  58 kB     00:00    
(547/602): tar-1.30-5.el8.x86_64.rpm            202 kB/s | 837 kB     00:04    
(548/602): trousers-0.3.15-1.el8.x86_64.rpm     436 kB/s | 151 kB     00:00    
(549/602): tuned-2.15.0-2.el8.noarch.rpm        743 kB/s | 302 kB     00:00    
(550/602): trousers-lib-0.3.15-1.el8.x86_64.rpm 185 kB/s | 166 kB     00:00    
(551/602): tzdata-2021a-1.el8.noarch.rpm        932 kB/s | 472 kB     00:00    
(552/602): usb_modeswitch-data-20191128-1.el8.n 313 kB/s | 108 kB     00:00    
(553/602): unzip-6.0-44.el8.x86_64.rpm          339 kB/s | 194 kB     00:00    
(554/602): usbutils-010-3.el8.x86_64.rpm        427 kB/s | 107 kB     00:00    
(555/602): userspace-rcu-0.10.1-4.el8.x86_64.rp 265 kB/s | 100 kB     00:00    
(556/602): util-linux-user-2.32.1-27.el8.x86_64 136 kB/s |  98 kB     00:00    
(557/602): util-linux-2.32.1-27.el8.x86_64.rpm  1.0 MB/s | 2.5 MB     00:02    
(558/602): vdo-6.2.4.14-14.el8.x86_64.rpm        50 kB/s | 589 kB     00:11    
(559/602): virt-what-1.18-6.el8.x86_64.rpm       90 kB/s |  34 kB     00:00    
(560/602): which-2.21-12.el8.x86_64.rpm          54 kB/s |  48 kB     00:00    
(561/602): words-3.0-28.el8.noarch.rpm          148 kB/s | 1.4 MB     00:09    
(562/602): xfsdump-3.1.8-2.el8.x86_64.rpm       466 kB/s | 331 kB     00:00    
(563/602): linux-firmware-20201218-102.git05789 793 kB/s | 123 MB     02:38    
(564/602): xfsprogs-5.0.0-8.el8.x86_64.rpm      531 kB/s | 1.1 MB     00:02    
(565/602): yum-4.4.2-11.el8.noarch.rpm          419 kB/s | 201 kB     00:00    
(566/602): zip-3.0-23.el8.x86_64.rpm            458 kB/s | 269 kB     00:00    
(567/602): zlib-1.2.11-17.el8.x86_64.rpm        686 kB/s | 101 kB     00:00    
(568/602): vim-minimal-8.0.1763-15.el8.x86_64.r  23 kB/s | 572 kB     00:24    
(569/602): kernel-4.18.0-305.3.1.el8_4.x86_64.r 648 kB/s | 5.9 MB     00:09    
(570/602): rsyslog-8.1911.0-7.el8.1.x86_64.rpm  868 kB/s | 730 kB     00:00    
(571/602): rsyslog-gnutls-8.1911.0-7.el8.1.x86_  81 kB/s |  30 kB     00:00    
(572/602): rsyslog-gssapi-8.1911.0-7.el8.1.x86_  96 kB/s |  32 kB     00:00    
(573/602): rsyslog-relp-8.1911.0-7.el8.1.x86_64  48 kB/s |  31 kB     00:00    
(574/602): acl-2.2.53-1.el8.1.x86_64.rpm        140 kB/s |  80 kB     00:00    
(575/602): audit-3.0-0.17.20191104git1c2f876.el 444 kB/s | 253 kB     00:00    
(576/602): audit-libs-3.0-0.17.20191104git1c2f8 182 kB/s | 116 kB     00:00    
(577/602): bpftool-4.18.0-305.3.1.el8_4.x86_64. 611 kB/s | 6.6 MB     00:10    
(578/602): e2fsprogs-1.45.6-1.el8.1.x86_64.rpm  450 kB/s | 1.0 MB     00:02    
(579/602): e2fsprogs-libs-1.45.6-1.el8.1.x86_64 357 kB/s | 232 kB     00:00    
(580/602): jimtcl-0.77-6.el8.1.x86_64.rpm       330 kB/s | 224 kB     00:00    
(581/602): kernel-tools-4.18.0-305.3.1.el8_4.x8 455 kB/s | 6.1 MB     00:13    
(582/602): kernel-modules-4.18.0-305.3.1.el8_4. 684 kB/s |  28 MB     00:42    
(583/602): libacl-2.2.53-1.el8.1.x86_64.rpm     114 kB/s |  33 kB     00:00    
(584/602): kernel-core-4.18.0-305.3.1.el8_4.x86 848 kB/s |  36 MB     00:43    
(585/602): libcom_err-1.45.6-1.el8.1.x86_64.rpm  77 kB/s |  48 kB     00:00    
(586/602): libreport-filesystem-2.9.5-15.el8.ro 124 kB/s |  20 kB     00:00    
(587/602): libss-1.45.6-1.el8.1.x86_64.rpm      270 kB/s |  52 kB     00:00    
(588/602): libnghttp2-1.33.0-3.el8_3.1.x86_64.r 106 kB/s |  76 kB     00:00    
(589/602): ncurses-base-6.1-7.20180224.el8.1.no 315 kB/s |  80 kB     00:00    
(590/602): ncurses-6.1-7.20180224.el8.1.x86_64. 426 kB/s | 386 kB     00:00    
(591/602): ncurses-libs-6.1-7.20180224.el8.1.x8 716 kB/s | 332 kB     00:00    
(592/602): platform-python-3.6.8-37.el8.rocky.x 241 kB/s |  84 kB     00:00    
(593/602): nettle-3.4.1-4.el8_4.x86_64.rpm      384 kB/s | 299 kB     00:00    
(594/602): python3-audit-3.0-0.17.20191104git1c 141 kB/s |  85 kB     00:00    
(595/602): kernel-tools-libs-4.18.0-305.3.1.el8 1.1 MB/s | 5.9 MB     00:05    
(596/602): platform-python-pip-9.0.3-19.el8.roc 732 kB/s | 1.7 MB     00:02    
(597/602): python3-pip-wheel-9.0.3-19.el8.rocky 741 kB/s | 1.0 MB     00:01    
(598/602): usb_modeswitch-2.5.2-1.el8.2.x86_64. 213 kB/s |  77 kB     00:00    
(599/602): xz-5.2.4-3.el8.1.x86_64.rpm          217 kB/s | 152 kB     00:00    
(600/602): xz-libs-5.2.4-3.el8.1.x86_64.rpm     198 kB/s |  93 kB     00:00    
(601/602): python3-libs-3.6.8-37.el8.rocky.x86_ 950 kB/s | 7.8 MB     00:08    
(602/602): python3-perf-4.18.0-305.3.1.el8_4.x8 767 kB/s | 6.0 MB     00:08    
--------------------------------------------------------------------------------
Total                                           1.6 MB/s | 540 MB     05:28     
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Running scriptlet: filesystem-3.8-3.el8.x86_64                            1/1 
  Running scriptlet: kmod-kvdo-6.2.4.26-77.el8.x86_64                       1/1 
  Preparing        :                                                        1/1 
  Running scriptlet: libgcc-8.4.1-1.el8.x86_64                              1/1 
  Reinstalling     : libgcc-8.4.1-1.el8.x86_64                           1/1201 
  Running scriptlet: libgcc-8.4.1-1.el8.x86_64                           1/1201 
  Reinstalling     : setup-2.12.2-6.el8.noarch                           2/1201 
warning: /etc/shadow created as /etc/shadow.rpmnew

  Running scriptlet: setup-2.12.2-6.el8.noarch                           2/1201 
  Reinstalling     : filesystem-3.8-3.el8.x86_64                         3/1201 
  Reinstalling     : hwdata-0.314-8.8.el8.noarch                         4/1201 
  Reinstalling     : fontpackages-filesystem-1.44-22.el8.noarch          5/1201 
  Reinstalling     : bind-license-32:9.11.26-4.el8_4.noarch              6/1201 
  Reinstalling     : abattis-cantarell-fonts-0.0.25-6.el8.noarch         7/1201 
  Upgrading        : python3-pip-wheel-9.0.3-19.el8.rocky.noarch         8/1201 
  Upgrading        : libreport-filesystem-2.9.5-15.el8.rocky.1.x86_      9/1201 
  Reinstalling     : tzdata-2021a-1.el8.noarch                          10/1201 
  Reinstalling     : python3-setuptools-wheel-39.2.0-6.el8.noarch       11/1201 
  Reinstalling     : geolite2-country-20180605-1.el8.noarch             12/1201 
  Reinstalling     : geolite2-city-20180605-1.el8.noarch                13/1201 
  Reinstalling     : dnf-data-4.4.2-11.el8.noarch                       14/1201 
  Reinstalling     : dejavu-fonts-common-2.35-7.el8.noarch              15/1201 
  Reinstalling     : dejavu-sans-mono-fonts-2.35-7.el8.noarch           16/1201 
  Reinstalling     : basesystem-11-5.el8.noarch                         17/1201 
  Upgrading        : ncurses-base-6.1-7.20180224.el8.1.noarch           18/1201 
  Reinstalling     : pcre2-10.32-2.el8.x86_64                           19/1201 
  Reinstalling     : libselinux-2.9-5.el8.x86_64                        20/1201 
  Running scriptlet: libselinux-2.9-5.el8.x86_64                        20/1201 
  Reinstalling     : glibc-langpack-en-2.28-151.el8.x86_64              21/1201 
  Reinstalling     : glibc-common-2.28-151.el8.x86_64                   22/1201 
  Running scriptlet: glibc-2.28-151.el8.x86_64                          23/1201 
  Reinstalling     : glibc-2.28-151.el8.x86_64                          23/1201 
  Running scriptlet: glibc-2.28-151.el8.x86_64                          23/1201 
  Upgrading        : ncurses-libs-6.1-7.20180224.el8.1.x86_64           24/1201 
  Reinstalling     : bash-4.4.20-1.el8_4.x86_64                         25/1201 
  Running scriptlet: bash-4.4.20-1.el8_4.x86_64                         25/1201 
  Reinstalling     : libsepol-2.9-2.el8.x86_64                          26/1201 
  Running scriptlet: libsepol-2.9-2.el8.x86_64                          26/1201 
  Reinstalling     : zlib-1.2.11-17.el8.x86_64                          27/1201 
  Upgrading        : libcom_err-1.45.6-1.el8.1.x86_64                   28/1201 
  Running scriptlet: libcom_err-1.45.6-1.el8.1.x86_64                   28/1201 
  Reinstalling     : popt-1.18-1.el8.x86_64                             29/1201 
  Reinstalling     : info-6.5-6.el8.x86_64                              30/1201 
  Reinstalling     : libcap-2.26-4.el8.x86_64                           31/1201 
  Reinstalling     : libuuid-2.32.1-27.el8.x86_64                       32/1201 
  Running scriptlet: libuuid-2.32.1-27.el8.x86_64                       32/1201 
  Upgrading        : xz-libs-5.2.4-3.el8.1.x86_64                       33/1201 
  Reinstalling     : libstdc++-8.4.1-1.el8.x86_64                       34/1201 
  Running scriptlet: libstdc++-8.4.1-1.el8.x86_64                       34/1201 
  Reinstalling     : libxml2-2.9.7-9.el8.x86_64                         35/1201 
  Reinstalling     : bzip2-libs-1.0.6-26.el8.x86_64                     36/1201 
  Reinstalling     : libgpg-error-1.31-1.el8.x86_64                     37/1201 
  Reinstalling     : libtalloc-2.3.1-2.el8.x86_64                       38/1201 
  Reinstalling     : libxcrypt-4.1.1-4.el8.x86_64                       39/1201 
  Reinstalling     : readline-7.0-10.el8.x86_64                         40/1201 
  Running scriptlet: readline-7.0-10.el8.x86_64                         40/1201 
  Reinstalling     : elfutils-libelf-0.182-3.el8.x86_64                 41/1201 
  Reinstalling     : sqlite-libs-3.26.0-13.el8.x86_64                   42/1201 
  Reinstalling     : libtevent-0.10.2-2.el8.x86_64                      43/1201 
  Reinstalling     : expat-2.2.5-4.el8.x86_64                           44/1201 
  Reinstalling     : libtdb-1.4.3-1.el8.x86_64                          45/1201 
  Running scriptlet: libtdb-1.4.3-1.el8.x86_64                          45/1201 
  Reinstalling     : pcre-8.42-4.el8.x86_64                             46/1201 
  Running scriptlet: pcre-8.42-4.el8.x86_64                             46/1201 
  Reinstalling     : grep-3.1-6.el8.x86_64                              47/1201 
  Running scriptlet: grep-3.1-6.el8.x86_64                              47/1201 
  Reinstalling     : chkconfig-1.13-2.el8.x86_64                        48/1201 
  Reinstalling     : libbasicobjects-0.1.1-39.el8.x86_64                49/1201 
  Reinstalling     : libcap-ng-0.7.9-5.el8.x86_64                       50/1201 
  Upgrading        : audit-libs-3.0-0.17.20191104git1c2f876.el8.1.x     51/1201 
  Reinstalling     : libcollection-0.7.0-39.el8.x86_64                  52/1201 
  Reinstalling     : libdhash-0.5.0-39.el8.x86_64                       53/1201 
  Reinstalling     : libref_array-0.1.5-39.el8.x86_64                   54/1201 
  Reinstalling     : libzstd-1.4.4-1.el8.x86_64                         55/1201 
  Reinstalling     : jansson-2.11-3.el8.x86_64                          56/1201 
  Reinstalling     : nspr-4.25.0-2.el8_2.x86_64                         57/1201 
  Running scriptlet: nspr-4.25.0-2.el8_2.x86_64                         57/1201 
  Reinstalling     : gmp-1:6.1.2-10.el8.x86_64                          58/1201 
  Running scriptlet: gmp-1:6.1.2-10.el8.x86_64                          58/1201 
  Reinstalling     : json-c-0.13.1-0.4.el8.x86_64                       59/1201 
  Reinstalling     : keyutils-libs-1.5.10-6.el8.x86_64                  60/1201 
  Reinstalling     : libattr-2.4.48-3.el8.x86_64                        61/1201 
  Upgrading        : libacl-2.2.53-1.el8.1.x86_64                       62/1201 
  Reinstalling     : sed-4.5-2.el8.x86_64                               63/1201 
  Running scriptlet: sed-4.5-2.el8.x86_64                               63/1201 
  Reinstalling     : libmnl-1.0.4-6.el8.x86_64                          64/1201 
  Running scriptlet: libmnl-1.0.4-6.el8.x86_64                          64/1201 
  Reinstalling     : libnl3-3.5.0-1.el8.x86_64                          65/1201 
  Running scriptlet: libnl3-3.5.0-1.el8.x86_64                          65/1201 
  Reinstalling     : libseccomp-2.5.1-1.el8.x86_64                      66/1201 
  Running scriptlet: libseccomp-2.5.1-1.el8.x86_64                      66/1201 
  Reinstalling     : lua-libs-5.3.4-11.el8.x86_64                       67/1201 
  Reinstalling     : nss-util-3.53.1-17.el8_3.x86_64                    68/1201 
  Reinstalling     : libassuan-2.5.1-3.el8.x86_64                       69/1201 
  Reinstalling     : libgcrypt-1.8.5-4.el8.x86_64                       70/1201 
  Running scriptlet: libgcrypt-1.8.5-4.el8.x86_64                       70/1201 
  Reinstalling     : libsss_idmap-2.4.0-9.el8.x86_64                    71/1201 
  Running scriptlet: libsss_idmap-2.4.0-9.el8.x86_64                    71/1201 
  Reinstalling     : which-2.21-12.el8.x86_64                           72/1201 
  Reinstalling     : libsemanage-2.9-6.el8.x86_64                       73/1201 
  Reinstalling     : findutils-1:4.6.0-20.el8.x86_64                    74/1201 
  Running scriptlet: findutils-1:4.6.0-20.el8.x86_64                    74/1201 
  Reinstalling     : libunistring-0.9.9-3.el8.x86_64                    75/1201 
  Reinstalling     : libidn2-2.2.0-1.el8.x86_64                         76/1201 
  Reinstalling     : file-libs-5.33-16.el8_3.1.x86_64                   77/1201 
  Reinstalling     : grub2-common-1:2.02-99.el8.noarch                  78/1201 
  Reinstalling     : libaio-0.3.112-1.el8.x86_64                        79/1201 
  Reinstalling     : libffi-3.1-22.el8.x86_64                           80/1201 
  Reinstalling     : p11-kit-0.23.22-1.el8.x86_64                       81/1201 
  Reinstalling     : libpng-2:1.6.34-5.el8.x86_64                       82/1201 
  Reinstalling     : freetype-2.9.1-4.el8_3.1.x86_64                    83/1201 
  Reinstalling     : libmaxminddb-1.2.0-10.el8.x86_64                   84/1201 
  Running scriptlet: libmaxminddb-1.2.0-10.el8.x86_64                   84/1201 
  Reinstalling     : protobuf-c-1.3.0-6.el8.x86_64                      85/1201 
  Reinstalling     : libsmartcols-2.32.1-27.el8.x86_64                  86/1201 
  Running scriptlet: libsmartcols-2.32.1-27.el8.x86_64                  86/1201 
  Reinstalling     : lz4-libs-1.8.3-2.el8.x86_64                        87/1201 
  Reinstalling     : pciutils-libs-3.7.0-1.el8.x86_64                   88/1201 
  Running scriptlet: pciutils-libs-3.7.0-1.el8.x86_64                   88/1201 
  Reinstalling     : file-5.33-16.el8_3.1.x86_64                        89/1201 
  Upgrading        : nettle-3.4.1-4.el8_4.x86_64                        90/1201 
  Running scriptlet: nettle-3.4.1-4.el8_4.x86_64                        90/1201 
  Reinstalling     : fstrm-0.6.0-3.el8.1.x86_64                         91/1201 
  Reinstalling     : pixman-0.38.4-1.el8.x86_64                         92/1201 
  Reinstalling     : gdbm-libs-1:1.18-1.el8.x86_64                      93/1201 
  Reinstalling     : libtasn1-4.13-3.el8.x86_64                         94/1201 
  Running scriptlet: libtasn1-4.13-3.el8.x86_64                         94/1201 
  Reinstalling     : p11-kit-trust-0.23.22-1.el8.x86_64                 95/1201 
  Running scriptlet: p11-kit-trust-0.23.22-1.el8.x86_64                 95/1201 
  Reinstalling     : device-mapper-persistent-data-0.8.5-4.el8.x86_     96/1201 
  Reinstalling     : libnl3-cli-3.5.0-1.el8.x86_64                      97/1201 
  Running scriptlet: libnl3-cli-3.5.0-1.el8.x86_64                      97/1201 
  Reinstalling     : ethtool-2:5.8-5.el8.x86_64                         98/1201 
  Reinstalling     : libnftnl-1.1.5-4.el8.x86_64                        99/1201 
  Running scriptlet: libnftnl-1.1.5-4.el8.x86_64                        99/1201 
  Reinstalling     : mpfr-3.1.6-1.el8.x86_64                           100/1201 
  Running scriptlet: mpfr-3.1.6-1.el8.x86_64                           100/1201 
  Upgrading        : xz-5.2.4-3.el8.1.x86_64                           101/1201 
  Reinstalling     : libmetalink-0.1.3-7.el8.x86_64                    102/1201 
  Reinstalling     : libksba-1.3.5-7.el8.x86_64                        103/1201 
  Reinstalling     : gdisk-1.0.3-6.el8.x86_64                          104/1201 
  Reinstalling     : diffutils-3.6-6.el8.x86_64                        105/1201 
  Running scriptlet: diffutils-3.6-6.el8.x86_64                        105/1201 
  Reinstalling     : libgomp-8.4.1-1.el8.x86_64                        106/1201 
  Running scriptlet: libgomp-8.4.1-1.el8.x86_64                        106/1201 
  Upgrading        : e2fsprogs-libs-1.45.6-1.el8.1.x86_64              107/1201 
  Running scriptlet: e2fsprogs-libs-1.45.6-1.el8.1.x86_64              107/1201 
  Reinstalling     : libselinux-utils-2.9-5.el8.x86_64                 108/1201 
  Reinstalling     : libedit-3.1-23.20170329cvs.el8.x86_64             109/1201 
  Reinstalling     : psmisc-23.1-5.el8.x86_64                          110/1201 
  Reinstalling     : cpio-2.12-10.el8.x86_64                           111/1201 
  Reinstalling     : dmidecode-1:3.2-8.el8.x86_64                      112/1201 
  Reinstalling     : libnfnetlink-1.0.1-13.el8.x86_64                  113/1201 
  Running scriptlet: libnfnetlink-1.0.1-13.el8.x86_64                  113/1201 
  Reinstalling     : libnetfilter_conntrack-1.0.6-5.el8.x86_64         114/1201 
  Running scriptlet: libnetfilter_conntrack-1.0.6-5.el8.x86_64         114/1201 
  Reinstalling     : libpath_utils-0.2.1-39.el8.x86_64                 115/1201 
  Reinstalling     : libini_config-1.3.1-39.el8.x86_64                 116/1201 
  Reinstalling     : libyaml-0.1.7-5.el8.x86_64                        117/1201 
  Reinstalling     : lzo-2.08-14.el8.x86_64                            118/1201 
  Reinstalling     : numactl-libs-2.0.12-11.el8.x86_64                 119/1201 
  Running scriptlet: numactl-libs-2.0.12-11.el8.x86_64                 119/1201 
  Reinstalling     : sg3_utils-libs-1.44-5.el8.x86_64                  120/1201 
  Running scriptlet: sg3_utils-libs-1.44-5.el8.x86_64                  120/1201 
  Reinstalling     : userspace-rcu-0.10.1-4.el8.x86_64                 121/1201 
  Running scriptlet: userspace-rcu-0.10.1-4.el8.x86_64                 121/1201 
  Reinstalling     : squashfs-tools-4.3-20.el8.x86_64                  122/1201 
  Reinstalling     : libbytesize-1.4-3.el8.x86_64                      123/1201 
  Reinstalling     : libteam-1.31-2.el8.x86_64                         124/1201 
  Running scriptlet: libteam-1.31-2.el8.x86_64                         124/1201 
  Reinstalling     : gdbm-1:1.18-1.el8.x86_64                          125/1201 
  Reinstalling     : ipcalc-0.2.4-4.el8.x86_64                         126/1201 
  Reinstalling     : grub2-pc-modules-1:2.02-99.el8.noarch             127/1201 
  Reinstalling     : libxslt-1.1.32-6.el8.x86_64                       128/1201 
  Reinstalling     : nss-softokn-freebl-3.53.1-17.el8_3.x86_64         129/1201 
  Reinstalling     : nss-softokn-3.53.1-17.el8_3.x86_64                130/1201 
  Reinstalling     : ipset-libs-7.1-1.el8.x86_64                       131/1201 
  Running scriptlet: ipset-libs-7.1-1.el8.x86_64                       131/1201 
  Reinstalling     : ipset-7.1-1.el8.x86_64                            132/1201 
  Reinstalling     : groff-base-1.22.3-18.el8.x86_64                   133/1201 
  Reinstalling     : tar-2:1.30-5.el8.x86_64                           134/1201 
  Running scriptlet: tar-2:1.30-5.el8.x86_64                           134/1201 
  Reinstalling     : vim-minimal-2:8.0.1763-15.el8.x86_64              135/1201 
  Upgrading        : acl-2.2.53-1.el8.1.x86_64                         136/1201 
  Reinstalling     : attr-2.4.48-3.el8.x86_64                          137/1201 
  Reinstalling     : libcomps-0.1.11-5.el8.x86_64                      138/1201 
  Reinstalling     : sqlite-3.26.0-13.el8.x86_64                       139/1201 
  Reinstalling     : bzip2-1.0.6-26.el8.x86_64                         140/1201 
  Reinstalling     : unzip-6.0-44.el8.x86_64                           141/1201 
  Reinstalling     : libconfig-1.5-9.el8.x86_64                        142/1201 
  Reinstalling     : libicu-60.3-2.el8_1.x86_64                        143/1201 
  Running scriptlet: libicu-60.3-2.el8_1.x86_64                        143/1201 
  Reinstalling     : libmodman-2.0.1-17.el8.x86_64                     144/1201 
  Running scriptlet: libmodman-2.0.1-17.el8.x86_64                     144/1201 
  Reinstalling     : libproxy-0.4.15-5.2.el8.x86_64                    145/1201 
  Running scriptlet: libproxy-0.4.15-5.2.el8.x86_64                    145/1201 
  Reinstalling     : mozjs60-60.9.0-4.el8.x86_64                       146/1201 
  Reinstalling     : snappy-1.1.8-3.el8.x86_64                         147/1201 
  Reinstalling     : coreutils-common-8.30-8.el8.x86_64                148/1201 
  Running scriptlet: coreutils-common-8.30-8.el8.x86_64                148/1201 
  Upgrading        : libss-1.45.6-1.el8.1.x86_64                       149/1201 
  Running scriptlet: libss-1.45.6-1.el8.1.x86_64                       149/1201 
  Reinstalling     : pigz-2.4-4.el8.x86_64                             150/1201 
  Reinstalling     : less-530-1.el8.x86_64                             151/1201 
  Upgrading        : kernel-tools-libs-4.18.0-305.3.1.el8_4.x86_64     152/1201 
  Running scriptlet: kernel-tools-libs-4.18.0-305.3.1.el8_4.x86_64     152/1201 
  Reinstalling     : memstrack-0.1.11-1.el8.x86_64                     153/1201 
  Upgrading        : ncurses-6.1-7.20180224.el8.1.x86_64               154/1201 
  Downgrading      : containernetworking-plugins-0.9.1-1.module+el8    155/1201 
  Reinstalling     : gpm-libs-1.20.7-17.el8.x86_64                     156/1201 
  Running scriptlet: gpm-libs-1.20.7-17.el8.x86_64                     156/1201 
  Reinstalling     : libXau-1.0.9-3.el8.x86_64                         157/1201 
  Reinstalling     : libxcb-1.13.1-1.el8.x86_64                        158/1201 
  Reinstalling     : libestr-0.1.10-1.el8.x86_64                       159/1201 
  Running scriptlet: libestr-0.1.10-1.el8.x86_64                       159/1201 
  Reinstalling     : libfastjson-0.99.8-2.el8.x86_64                   160/1201 
  Running scriptlet: libfastjson-0.99.8-2.el8.x86_64                   160/1201 
  Reinstalling     : libnet-1.1.6-15.el8.x86_64                        161/1201 
  Running scriptlet: libnet-1.1.6-15.el8.x86_64                        161/1201 
  Downgrading      : criu-3.15-1.module+el8.4.0+556+40122d08.x86_64    162/1201 
  Downgrading      : runc-1.0.0-73.rc93.module+el8.4.0+556+40122d08    163/1201 
  Reinstalling     : oniguruma-6.8.2-2.el8.x86_64                      164/1201 
  Running scriptlet: oniguruma-6.8.2-2.el8.x86_64                      164/1201 
  Reinstalling     : jq-1.5-12.el8.x86_64                              165/1201 
  Reinstalling     : yajl-2.1.0-10.el8.x86_64                          166/1201 
  Reinstalling     : brotli-1.0.6-3.el8.x86_64                         167/1201 
  Reinstalling     : c-ares-1.13.0-5.el8.x86_64                        168/1201 
  Running scriptlet: c-ares-1.13.0-5.el8.x86_64                        168/1201 
  Reinstalling     : checkpolicy-2.9-1.el8.x86_64                      169/1201 
  Reinstalling     : dosfstools-4.1-6.el8.x86_64                       170/1201 
  Reinstalling     : fuse-libs-2.9.7-12.el8.x86_64                     171/1201 
  Running scriptlet: fuse-libs-2.9.7-12.el8.x86_64                     171/1201 
  Reinstalling     : fuse3-libs-3.2.1-12.el8.x86_64                    172/1201 
  Running scriptlet: fuse3-libs-3.2.1-12.el8.x86_64                    172/1201 
  Reinstalling     : hardlink-1:1.3-6.el8.x86_64                       173/1201 
  Reinstalling     : hdparm-9.54-3.el8.x86_64                          174/1201 
  Reinstalling     : libdaemon-0.14-15.el8.x86_64                      175/1201 
  Reinstalling     : libndp-1.7-5.el8.x86_64                           176/1201 
  Running scriptlet: libndp-1.7-5.el8.x86_64                           176/1201 
  Reinstalling     : libpipeline-1.5.0-2.el8.x86_64                    177/1201 
  Running scriptlet: libpipeline-1.5.0-2.el8.x86_64                    177/1201 
  Reinstalling     : libpkgconf-1.4.2-1.el8.x86_64                     178/1201 
  Reinstalling     : pkgconf-1.4.2-1.el8.x86_64                        179/1201 
  Reinstalling     : libsigsegv-2.11-5.el8.x86_64                      180/1201 
  Reinstalling     : gawk-4.2.1-2.el8.x86_64                           181/1201 
  Reinstalling     : libsss_autofs-2.4.0-9.el8.x86_64                  182/1201 
  Reinstalling     : libsss_nss_idmap-2.4.0-9.el8.x86_64               183/1201 
  Running scriptlet: libsss_nss_idmap-2.4.0-9.el8.x86_64               183/1201 
  Reinstalling     : libsss_sudo-2.4.0-9.el8.x86_64                    184/1201 
  Running scriptlet: libsss_sudo-2.4.0-9.el8.x86_64                    184/1201 
  Reinstalling     : libstemmer-0-10.585svn.el8.x86_64                 185/1201 
  Running scriptlet: libstemmer-0-10.585svn.el8.x86_64                 185/1201 
  Reinstalling     : libverto-0.3.0-5.el8.x86_64                       186/1201 
  Reinstalling     : lmdb-libs-0.9.24-1.el8.x86_64                     187/1201 
  Reinstalling     : npth-1.5-4.el8.x86_64                             188/1201 
  Reinstalling     : slang-2.3.2-3.el8.x86_64                          189/1201 
  Reinstalling     : newt-0.52.20-11.el8.x86_64                        190/1201 
  Upgrading        : jimtcl-0.77-6.el8.1.x86_64                        191/1201 
  Running scriptlet: jimtcl-0.77-6.el8.1.x86_64                        191/1201 
  Upgrading        : libnghttp2-1.33.0-3.el8_3.1.x86_64                192/1201 
  Reinstalling     : quota-nls-1:4.04-12.el8.noarch                    193/1201 
  Reinstalling     : publicsuffix-list-dafsa-20180723-1.el8.noarch     194/1201 
  Reinstalling     : libpsl-0.20.2-6.el8.x86_64                        195/1201 
  Reinstalling     : pkgconf-m4-1.4.2-1.el8.noarch                     196/1201 
  Reinstalling     : pkgconf-pkg-config-1.4.2-1.el8.x86_64             197/1201 
  Reinstalling     : linux-firmware-20201218-102.git05789708.el8.no    198/1201 
  Reinstalling     : libssh-config-0.9.4-2.el8.noarch                  199/1201 
  Reinstalling     : kbd-misc-2.0.4-10.el8.noarch                      200/1201 
  Reinstalling     : kbd-legacy-2.0.4-10.el8.noarch                    201/1201 
  Reinstalling     : fuse-common-3.2.1-12.el8.x86_64                   202/1201 
  Reinstalling     : fuse3-3.2.1-12.el8.x86_64                         203/1201 
  Reinstalling     : firewalld-filesystem-0.8.2-6.el8.noarch           204/1201 
  Reinstalling     : emacs-filesystem-1:26.1-5.el8.noarch              205/1201 
  Reinstalling     : dbus-common-1:1.12.8-12.el8_4.2.noarch            206/1201 
  Reinstalling     : xkeyboard-config-2.28-1.el8.noarch                207/1201 
  Reinstalling     : libxkbcommon-0.9.1-1.el8.x86_64                   208/1201 
  Reinstalling     : pciutils-3.7.0-1.el8.x86_64                       209/1201 
  Reinstalling     : cyrus-sasl-lib-2.1.27-5.el8.x86_64                210/1201 
  Running scriptlet: cyrus-sasl-lib-2.1.27-5.el8.x86_64                210/1201 
  Reinstalling     : platform-python-setuptools-39.2.0-6.el8.noarch    211/1201 
  Upgrading        : platform-python-pip-9.0.3-19.el8.rocky.noarch     212/1201 
  Upgrading        : python3-libs-3.6.8-37.el8.rocky.x86_64            213/1201 
  Reinstalling     : grub2-tools-minimal-1:2.02-99.el8.x86_64          214/1201 
  Reinstalling     : rdma-core-32.0-4.el8.x86_64                       215/1201 
  Running scriptlet: rdma-core-32.0-4.el8.x86_64                       215/1201 
  Reinstalling     : libibverbs-32.0-4.el8.x86_64                      216/1201 
  Running scriptlet: libibverbs-32.0-4.el8.x86_64                      216/1201 
  Reinstalling     : libpcap-14:1.9.1-5.el8.x86_64                     217/1201 
  Reinstalling     : iptables-libs-1.8.4-17.el8.x86_64                 218/1201 
  Reinstalling     : libssh-0.9.4-2.el8.x86_64                         219/1201 
  Reinstalling     : openldap-2.4.46-16.el8.x86_64                     220/1201 
  Upgrading        : platform-python-3.6.8-37.el8.rocky.x86_64         221/1201 
  Running scriptlet: platform-python-3.6.8-37.el8.rocky.x86_64         221/1201 
  Reinstalling     : grubby-8.40-41.el8.x86_64                         222/1201 
  Reinstalling     : libkcapi-1.2.0-2.el8.x86_64                       223/1201 
  Reinstalling     : libkcapi-hmaccalc-1.2.0-2.el8.x86_64              224/1201 
  Reinstalling     : libarchive-3.3.3-1.el8.x86_64                     225/1201 
  Reinstalling     : libdb-utils-5.3.28-40.el8.x86_64                  226/1201 
  Reinstalling     : curl-7.61.1-18.el8.x86_64                         227/1201 
  Reinstalling     : libcurl-7.61.1-18.el8.x86_64                      228/1201 
  Reinstalling     : openssl-1:1.1.1g-15.el8_3.x86_64                  229/1201 
  Reinstalling     : crypto-policies-scripts-20210209-1.gitbfb6bed.    230/1201 
  Reinstalling     : crypto-policies-20210209-1.gitbfb6bed.el8_3.no    231/1201 
  Running scriptlet: crypto-policies-20210209-1.gitbfb6bed.el8_3.no    231/1201 
  Reinstalling     : elfutils-default-yama-scope-0.182-3.el8.noarch    232/1201 
  Running scriptlet: elfutils-default-yama-scope-0.182-3.el8.noarch    232/1201 
  Reinstalling     : gzip-1.9-12.el8.x86_64                            233/1201 
  Running scriptlet: gzip-1.9-12.el8.x86_64                            233/1201 
  Reinstalling     : cracklib-2.9.6-15.el8.x86_64                      234/1201 
  Reinstalling     : cracklib-dicts-2.9.6-15.el8.x86_64                235/1201 
  Reinstalling     : procps-ng-3.3.15-6.el8.x86_64                     236/1201 
  Reinstalling     : krb5-libs-1.18.2-8.el8.x86_64                     237/1201 
  Reinstalling     : libtirpc-1.1.4-4.el8.x86_64                       238/1201 
  Running scriptlet: libtirpc-1.1.4-4.el8.x86_64                       238/1201 
  Reinstalling     : libnsl2-1.2.0-2.20180605git4a062cf.el8.x86_64     239/1201 
  Running scriptlet: libnsl2-1.2.0-2.20180605git4a062cf.el8.x86_64     239/1201 
  Reinstalling     : kpartx-0.8.4-10.el8.x86_64                        240/1201 
  Reinstalling     : device-mapper-8:1.02.175-5.el8.x86_64             241/1201 
  Reinstalling     : elfutils-debuginfod-client-0.182-3.el8.x86_64     242/1201 
  Reinstalling     : elfutils-libs-0.182-3.el8.x86_64                  243/1201 
  Reinstalling     : openssl-pkcs11-0.4.10-2.el8.x86_64                244/1201 
  Reinstalling     : rpm-4.14.3-13.el8.x86_64                          245/1201 
  Reinstalling     : gettext-libs-0.19.8.1-17.el8.x86_64               246/1201 
  Reinstalling     : libcroco-0.6.12-4.el8_2.1.x86_64                  247/1201 
  Running scriptlet: libcroco-0.6.12-4.el8_2.1.x86_64                  247/1201 
  Reinstalling     : libfdisk-2.32.1-27.el8.x86_64                     248/1201 
  Running scriptlet: libfdisk-2.32.1-27.el8.x86_64                     248/1201 
  Reinstalling     : libmount-2.32.1-27.el8.x86_64                     249/1201 
  Running scriptlet: libmount-2.32.1-27.el8.x86_64                     249/1201 
  Reinstalling     : dbus-libs-1:1.12.8-12.el8_4.2.x86_64              250/1201 
  Running scriptlet: dbus-libs-1:1.12.8-12.el8_4.2.x86_64              250/1201 
  Reinstalling     : dbus-tools-1:1.12.8-12.el8_4.2.x86_64             251/1201 
  Reinstalling     : coreutils-8.30-8.el8.x86_64                       252/1201 
  Reinstalling     : systemd-libs-239-45.el8.x86_64                    253/1201 
  Running scriptlet: systemd-libs-239-45.el8.x86_64                    253/1201 
  Reinstalling     : libblkid-2.32.1-27.el8.x86_64                     254/1201 
  Running scriptlet: libblkid-2.32.1-27.el8.x86_64                     254/1201 
  Reinstalling     : shadow-utils-2:4.6-12.el8.x86_64                  255/1201 
  Reinstalling     : device-mapper-libs-8:1.02.175-5.el8.x86_64        256/1201 
  Running scriptlet: ca-certificates-2020.2.41-80.0.el8_2.noarch       257/1201 
  Reinstalling     : ca-certificates-2020.2.41-80.0.el8_2.noarch       257/1201 
  Running scriptlet: ca-certificates-2020.2.41-80.0.el8_2.noarch       257/1201 
  Reinstalling     : openssl-libs-1:1.1.1g-15.el8_3.x86_64             258/1201 
  Running scriptlet: openssl-libs-1:1.1.1g-15.el8_3.x86_64             258/1201 
  Reinstalling     : kmod-libs-25-17.el8.x86_64                        259/1201 
  Running scriptlet: kmod-libs-25-17.el8.x86_64                        259/1201 
  Reinstalling     : libdb-5.3.28-40.el8.x86_64                        260/1201 
  Running scriptlet: libdb-5.3.28-40.el8.x86_64                        260/1201 
  Reinstalling     : rpm-libs-4.14.3-13.el8.x86_64                     261/1201 
  Running scriptlet: rpm-libs-4.14.3-13.el8.x86_64                     261/1201 
  Reinstalling     : kmod-25-17.el8.x86_64                             262/1201 
  Reinstalling     : cryptsetup-libs-2.3.3-4.el8.x86_64                263/1201 
  Running scriptlet: cryptsetup-libs-2.3.3-4.el8.x86_64                263/1201 
  Reinstalling     : trousers-lib-0.3.15-1.el8.x86_64                  264/1201 
  Running scriptlet: trousers-lib-0.3.15-1.el8.x86_64                  264/1201 
  Running scriptlet: dbus-daemon-1:1.12.8-12.el8_4.2.x86_64            265/1201 
  Reinstalling     : dbus-daemon-1:1.12.8-12.el8_4.2.x86_64            265/1201 
  Running scriptlet: dbus-daemon-1:1.12.8-12.el8_4.2.x86_64            265/1201 
  Running scriptlet: libutempter-1.1.6-14.el8.x86_64                   266/1201 
  Reinstalling     : libutempter-1.1.6-14.el8.x86_64                   266/1201 
  Reinstalling     : kbd-2.0.4-10.el8.x86_64                           267/1201 
  Reinstalling     : libpwquality-1.4.4-3.el8.x86_64                   268/1201 
  Reinstalling     : pam-1.3.1-14.el8.x86_64                           269/1201 
  Running scriptlet: pam-1.3.1-14.el8.x86_64                           269/1201 
  Reinstalling     : util-linux-2.32.1-27.el8.x86_64                   270/1201 
  Running scriptlet: util-linux-2.32.1-27.el8.x86_64                   270/1201 
  Reinstalling     : systemd-pam-239-45.el8.x86_64                     271/1201 
  Reinstalling     : dracut-049-135.git20210121.el8.x86_64             272/1201 
  Reinstalling     : os-prober-1.74-6.el8.x86_64                       273/1201 
  Reinstalling     : gettext-0.19.8.1-17.el8.x86_64                    274/1201 
  Running scriptlet: gettext-0.19.8.1-17.el8.x86_64                    274/1201 
  Running scriptlet: grub2-tools-1:2.02-99.el8.x86_64                  275/1201 
  Reinstalling     : grub2-tools-1:2.02-99.el8.x86_64                  275/1201 
  Running scriptlet: grub2-tools-1:2.02-99.el8.x86_64                  275/1201 
  Reinstalling     : glib2-2.56.4-10.el8_4.x86_64                      276/1201 
  Reinstalling     : shared-mime-info-1.9-3.el8.x86_64                 277/1201 
  Running scriptlet: shared-mime-info-1.9-3.el8.x86_64                 277/1201 
  Reinstalling     : gnutls-3.6.14-8.el8_3.x86_64                      278/1201 
  Reinstalling     : dbus-1:1.12.8-12.el8_4.2.x86_64                   279/1201 
  Running scriptlet: systemd-239-45.el8.x86_64                         280/1201 
  Reinstalling     : systemd-239-45.el8.x86_64                         280/1201 
  Running scriptlet: systemd-239-45.el8.x86_64                         280/1201 
  Reinstalling     : systemd-udev-239-45.el8.x86_64                    281/1201 
  Running scriptlet: systemd-udev-239-45.el8.x86_64                    281/1201 
  Running scriptlet: trousers-0.3.15-1.el8.x86_64                      282/1201 
  Reinstalling     : trousers-0.3.15-1.el8.x86_64                      282/1201 
  Running scriptlet: trousers-0.3.15-1.el8.x86_64                      282/1201 
  Reinstalling     : polkit-libs-0.115-11.el8_4.1.x86_64               283/1201 
  Running scriptlet: polkit-libs-0.115-11.el8_4.1.x86_64               283/1201 
  Reinstalling     : libldb-2.2.0-2.el8.x86_64                         284/1201 
  Reinstalling     : python3-six-1.11.0-8.el8.noarch                   285/1201 
  Running scriptlet: polkit-0.115-11.el8_4.1.x86_64                    286/1201 
  Reinstalling     : polkit-0.115-11.el8_4.1.x86_64                    286/1201 
  Running scriptlet: polkit-0.115-11.el8_4.1.x86_64                    286/1201 
  Reinstalling     : polkit-pkla-compat-0.1-12.el8.x86_64              287/1201 
  Reinstalling     : python3-libselinux-2.9-5.el8.x86_64               288/1201 
  Reinstalling     : libmodulemd-2.9.4-2.el8.x86_64                    289/1201 
  Reinstalling     : policycoreutils-2.9-14.el8.x86_64                 290/1201 
  Running scriptlet: policycoreutils-2.9-14.el8.x86_64                 290/1201 
  Reinstalling     : libsss_certmap-2.4.0-9.el8.x86_64                 291/1201 
  Running scriptlet: libsss_certmap-2.4.0-9.el8.x86_64                 291/1201 
  Reinstalling     : device-mapper-event-libs-8:1.02.175-5.el8.x86_    292/1201 
  Reinstalling     : libusbx-1.0.23-4.el8.x86_64                       293/1201 
  Running scriptlet: iptables-1.8.4-17.el8.x86_64                      294/1201 
  Reinstalling     : iptables-1.8.4-17.el8.x86_64                      294/1201 
  Running scriptlet: iptables-1.8.4-17.el8.x86_64                      294/1201 
  Installing       : kernel-core-4.18.0-305.3.1.el8_4.x86_64           295/1201 
  Running scriptlet: kernel-core-4.18.0-305.3.1.el8_4.x86_64           295/1201 
  Reinstalling     : gobject-introspection-1.56.1-1.el8.x86_64         296/1201 
  Reinstalling     : python3-gobject-base-3.28.3-2.el8.x86_64          297/1201 
  Reinstalling     : json-glib-1.4.4-1.el8.x86_64                      298/1201 
  Reinstalling     : libgudev-232-4.el8.x86_64                         299/1201 
  Reinstalling     : libsolv-0.7.16-2.el8.x86_64                       300/1201 
  Reinstalling     : parted-3.2-38.el8.x86_64                          301/1201 
  Running scriptlet: parted-3.2-38.el8.x86_64                          301/1201 
  Reinstalling     : libblockdev-utils-2.24-5.el8.x86_64               302/1201 
  Running scriptlet: logrotate-3.14.0-4.el8.x86_64                     303/1201 
  Reinstalling     : logrotate-3.14.0-4.el8.x86_64                     303/1201 
  Running scriptlet: samba-common-4.13.3-3.el8.noarch                  304/1201 
  Reinstalling     : samba-common-4.13.3-3.el8.noarch                  304/1201 
  Running scriptlet: samba-common-4.13.3-3.el8.noarch                  304/1201 
  Upgrading        : rsyslog-8.1911.0-7.el8.1.x86_64                   305/1201 
  Running scriptlet: rsyslog-8.1911.0-7.el8.1.x86_64                   305/1201 
  Reinstalling     : python3-decorator-4.2.1-2.el8.noarch              306/1201 
  Reinstalling     : rpm-plugin-selinux-4.14.3-13.el8.x86_64           307/1201 
  Reinstalling     : selinux-policy-3.14.3-67.el8.noarch               308/1201 
  Running scriptlet: selinux-policy-3.14.3-67.el8.noarch               308/1201 
  Running scriptlet: selinux-policy-targeted-3.14.3-67.el8.noarch      309/1201 
  Reinstalling     : selinux-policy-targeted-3.14.3-67.el8.noarch      309/1201 
  Running scriptlet: selinux-policy-targeted-3.14.3-67.el8.noarch      309/1201 
  Reinstalling     : crontabs-1.11-17.20190603git.el8.noarch           310/1201 
  Reinstalling     : cronie-1.5.2-4.el8.x86_64                         311/1201 
  Running scriptlet: cronie-1.5.2-4.el8.x86_64                         311/1201 
  Reinstalling     : cronie-anacron-1.5.2-4.el8.x86_64                 312/1201 
  Running scriptlet: cronie-anacron-1.5.2-4.el8.x86_64                 312/1201 
  Reinstalling     : initscripts-10.00.15-1.el8.x86_64                 313/1201 
  Running scriptlet: initscripts-10.00.15-1.el8.x86_64                 313/1201 
  Reinstalling     : iputils-20180629-7.el8.x86_64                     314/1201 
  Running scriptlet: iputils-20180629-7.el8.x86_64                     314/1201 
  Running scriptlet: libstoragemgmt-1.8.7-1.el8.x86_64                 315/1201 
  Reinstalling     : libstoragemgmt-1.8.7-1.el8.x86_64                 315/1201 
  Running scriptlet: libstoragemgmt-1.8.7-1.el8.x86_64                 315/1201 
  Reinstalling     : python3-libstoragemgmt-clibs-1.8.7-1.el8.x86_6    316/1201 
  Reinstalling     : python3-libstoragemgmt-1.8.7-1.el8.noarch         317/1201 
  Reinstalling     : NetworkManager-libnm-1:1.30.0-7.el8.x86_64        318/1201 
  Running scriptlet: NetworkManager-libnm-1:1.30.0-7.el8.x86_64        318/1201 
  Running scriptlet: NetworkManager-1:1.30.0-7.el8.x86_64              319/1201 
  Reinstalling     : NetworkManager-1:1.30.0-7.el8.x86_64              319/1201 
  Running scriptlet: NetworkManager-1:1.30.0-7.el8.x86_64              319/1201 
  Reinstalling     : gdk-pixbuf2-2.36.12-5.el8.x86_64                  320/1201 
  Running scriptlet: gdk-pixbuf2-2.36.12-5.el8.x86_64                  320/1201 
  Reinstalling     : libuser-0.62-23.el8.x86_64                        321/1201 
  Running scriptlet: libuser-0.62-23.el8.x86_64                        321/1201 
  Running scriptlet: openssh-8.0p1-6.el8_4.2.x86_64                    322/1201 
  Reinstalling     : openssh-8.0p1-6.el8_4.2.x86_64                    322/1201 
  Downgrading      : fuse-overlayfs-1.4.0-3.module+el8.4.0+556+4012    323/1201 
  Running scriptlet: fuse-overlayfs-1.4.0-3.module+el8.4.0+556+4012    323/1201 
  Reinstalling     : iproute-5.9.0-4.el8.x86_64                        324/1201 
  Reinstalling     : bind-libs-lite-32:9.11.26-4.el8_4.x86_64          325/1201 
  Reinstalling     : libjose-10-2.el8.x86_64                           326/1201 
  Running scriptlet: libjose-10-2.el8.x86_64                           326/1201 
  Reinstalling     : libevent-2.1.8-5.el8.x86_64                       327/1201 
  Running scriptlet: tpm2-tss-2.3.2-3.el8.x86_64                       328/1201 
  Reinstalling     : tpm2-tss-2.3.2-3.el8.x86_64                       328/1201 
  Running scriptlet: tpm2-tss-2.3.2-3.el8.x86_64                       328/1201 
  Reinstalling     : ima-evm-utils-1.3.2-12.el8.x86_64                 329/1201 
  Reinstalling     : xfsprogs-5.0.0-8.el8.x86_64                       330/1201 
  Running scriptlet: xfsprogs-5.0.0-8.el8.x86_64                       330/1201 
  Downgrading      : crun-0.18-2.module+el8.4.0+556+40122d08.x86_64    331/1201 
  Reinstalling     : fontconfig-2.13.1-3.el8.x86_64                    332/1201 
  Running scriptlet: fontconfig-2.13.1-3.el8.x86_64                    332/1201 
  Reinstalling     : avahi-libs-0.7-20.el8.x86_64                      333/1201 
  Reinstalling     : cyrus-sasl-gssapi-2.1.27-5.el8.x86_64             334/1201 
  Reinstalling     : python3-libxml2-2.9.7-9.el8.x86_64                335/1201 
  Upgrading        : python3-audit-3.0-0.17.20191104git1c2f876.el8.    336/1201 
  Reinstalling     : nftables-1:0.9.3-18.el8.x86_64                    337/1201 
  Running scriptlet: nftables-1:0.9.3-18.el8.x86_64                    337/1201 
  Reinstalling     : python3-nftables-1:0.9.3-18.el8.x86_64            338/1201 
  Reinstalling     : adcli-0.8.2-9.el8.x86_64                          339/1201 
  Running scriptlet: adcli-0.8.2-9.el8.x86_64                          339/1201 
  Reinstalling     : cups-libs-1:2.2.6-38.el8.x86_64                   340/1201 
  Reinstalling     : libwbclient-4.13.3-3.el8.x86_64                   341/1201 
  Reinstalling     : samba-common-libs-4.13.3-3.el8.x86_64             342/1201 
  Reinstalling     : samba-client-libs-4.13.3-3.el8.x86_64             343/1201 
  Reinstalling     : libsmbclient-4.13.3-3.el8.x86_64                  344/1201 
  Reinstalling     : tpm2-tools-4.1.1-2.el8.x86_64                     345/1201 
  Running scriptlet: unbound-libs-1.7.3-15.el8.x86_64                  346/1201 
  Reinstalling     : unbound-libs-1.7.3-15.el8.x86_64                  346/1201 
  Running scriptlet: unbound-libs-1.7.3-15.el8.x86_64                  346/1201 
  Reinstalling     : python3-unbound-1.7.3-15.el8.x86_64               347/1201 
  Reinstalling     : jose-10-2.el8.x86_64                              348/1201 
  Running scriptlet: clevis-15-1.el8.x86_64                            349/1201 
  Reinstalling     : clevis-15-1.el8.x86_64                            349/1201 
  Reinstalling     : bind-libs-32:9.11.26-4.el8_4.x86_64               350/1201 
  Upgrading        : audit-3.0-0.17.20191104git1c2f876.el8.1.x86_64    351/1201 
  Running scriptlet: audit-3.0-0.17.20191104git1c2f876.el8.1.x86_64    351/1201 
  Reinstalling     : libblockdev-2.24-5.el8.x86_64                     352/1201 
  Reinstalling     : libblockdev-fs-2.24-5.el8.x86_64                  353/1201 
  Reinstalling     : libblockdev-loop-2.24-5.el8.x86_64                354/1201 
  Reinstalling     : libblockdev-part-2.24-5.el8.x86_64                355/1201 
  Reinstalling     : libblockdev-swap-2.24-5.el8.x86_64                356/1201 
  Reinstalling     : python3-pydbus-0.6.0-5.el8.noarch                 357/1201 
  Reinstalling     : PackageKit-glib-1.1.12-6.el8.x86_64               358/1201 
  Running scriptlet: kmod-kvdo-6.2.4.26-77.el8.x86_64                  359/1201 
  Reinstalling     : kmod-kvdo-6.2.4.26-77.el8.x86_64                  359/1201 
  Running scriptlet: kmod-kvdo-6.2.4.26-77.el8.x86_64                  359/1201 
  Installing       : kernel-modules-4.18.0-305.3.1.el8_4.x86_64        360/1201 
  Running scriptlet: kernel-modules-4.18.0-305.3.1.el8_4.x86_64        360/1201 
  Reinstalling     : iptables-ebtables-1.8.4-17.el8.x86_64             361/1201 
  Running scriptlet: iptables-ebtables-1.8.4-17.el8.x86_64             361/1201 
  Reinstalling     : libgusb-0.3.0-1.el8.x86_64                        362/1201 
  Reinstalling     : usb_modeswitch-data-20191128-1.el8.noarch         363/1201 
  Running scriptlet: usb_modeswitch-data-20191128-1.el8.noarch         363/1201 
  Upgrading        : usb_modeswitch-2.5.2-1.el8.2.x86_64               364/1201 
  Reinstalling     : device-mapper-event-8:1.02.175-5.el8.x86_64       365/1201 
  Running scriptlet: device-mapper-event-8:1.02.175-5.el8.x86_64       365/1201 
  Reinstalling     : lvm2-libs-8:2.03.11-5.el8.x86_64                  366/1201 
  Reinstalling     : lvm2-8:2.03.11-5.el8.x86_64                       367/1201 
  Running scriptlet: lvm2-8:2.03.11-5.el8.x86_64                       367/1201 
  Reinstalling     : libblockdev-lvm-2.24-5.el8.x86_64                 368/1201 
  Reinstalling     : python3-libsemanage-2.9-6.el8.x86_64              369/1201 
  Reinstalling     : python3-setools-4.3.0-2.el8.x86_64                370/1201 
  Reinstalling     : python3-policycoreutils-2.9-14.el8.noarch         371/1201 
  Reinstalling     : policycoreutils-python-utils-2.9-14.el8.noarch    372/1201 
  Running scriptlet: container-selinux-2:2.162.0-1.module+el8.4.0+5    373/1201 
  Downgrading      : container-selinux-2:2.162.0-1.module+el8.4.0+5    373/1201 
  Running scriptlet: container-selinux-2:2.162.0-1.module+el8.4.0+5    373/1201 
  Reinstalling     : python3-slip-0.6.4-11.el8.noarch                  374/1201 
  Reinstalling     : timedatex-0.5-3.el8.x86_64                        375/1201 
  Running scriptlet: timedatex-0.5-3.el8.x86_64                        375/1201 
  Reinstalling     : python3-configobj-5.0.6-11.el8.noarch             376/1201 
  Reinstalling     : python3-dateutil-1:2.6.1-6.el8.noarch             377/1201 
  Reinstalling     : python3-linux-procfs-0.6.3-1.el8.noarch           378/1201 
  Reinstalling     : python3-pyudev-0.21.0-7.el8.noarch                379/1201 
  Reinstalling     : oddjob-0.34.7-1.el8.x86_64                        380/1201 
  Running scriptlet: oddjob-0.34.7-1.el8.x86_64                        380/1201 
  Reinstalling     : oddjob-mkhomedir-0.34.7-1.el8.x86_64              381/1201 
  Running scriptlet: oddjob-mkhomedir-0.34.7-1.el8.x86_64              381/1201 
  Running scriptlet: authselect-libs-1.2.2-2.el8.x86_64                382/1201 
  Reinstalling     : authselect-libs-1.2.2-2.el8.x86_64                382/1201 
  Reinstalling     : mdadm-4.1-15.el8.x86_64                           383/1201 
  Running scriptlet: mdadm-4.1-15.el8.x86_64                           383/1201 
  Reinstalling     : libblockdev-mdraid-2.24-5.el8.x86_64              384/1201 
  Reinstalling     : librelp-1.2.16-1.el8.x86_64                       385/1201 
  Running scriptlet: librelp-1.2.16-1.el8.x86_64                       385/1201 
  Downgrading      : conmon-2:2.0.26-3.module+el8.4.0+556+40122d08.    386/1201 
  Downgrading      : libslirp-4.3.1-1.module+el8.4.0+556+40122d08.x    387/1201 
  Downgrading      : slirp4netns-1.1.8-1.module+el8.4.0+556+40122d0    388/1201 
  Downgrading      : containers-common-1:1.2.2-10.module+el8.4.0+55    389/1201 
  Reinstalling     : desktop-file-utils-0.23-8.el8.x86_64              390/1201 
  Reinstalling     : xdg-utils-1.1.2-5.el8.noarch                      391/1201 
  Reinstalling     : libudisks2-2.9.0-6.el8.x86_64                     392/1201 
  Reinstalling     : dbus-glib-0.110-2.el8.x86_64                      393/1201 
  Running scriptlet: dbus-glib-0.110-2.el8.x86_64                      393/1201 
  Reinstalling     : python3-dbus-1.2.4-15.el8.x86_64                  394/1201 
  Reinstalling     : python3-slip-dbus-0.6.4-11.el8.noarch             395/1201 
  Reinstalling     : python3-firewall-0.8.2-6.el8.noarch               396/1201 
  Reinstalling     : gsettings-desktop-schemas-3.32.0-5.el8.x86_64     397/1201 
  Reinstalling     : glib-networking-2.56.1-1.1.el8.x86_64             398/1201 
  Reinstalling     : cockpit-bridge-238.2-1.el8.x86_64                 399/1201 
  Reinstalling     : libsoup-2.62.3-2.el8.x86_64                       400/1201 
  Reinstalling     : libappstream-glib-0.7.14-3.el8.x86_64             401/1201 
  Reinstalling     : libipa_hbac-2.4.0-9.el8.x86_64                    402/1201 
  Running scriptlet: libipa_hbac-2.4.0-9.el8.x86_64                    402/1201 
  Reinstalling     : libsecret-0.18.6-1.el8.x86_64                     403/1201 
  Reinstalling     : pinentry-1.1.0-2.el8.x86_64                       404/1201 
  Running scriptlet: pinentry-1.1.0-2.el8.x86_64                       404/1201 
  Reinstalling     : gnupg2-smime-2.2.20-2.el8.x86_64                  405/1201 
  Reinstalling     : gnupg2-2.2.20-2.el8.x86_64                        406/1201 
  Reinstalling     : gpgme-1.13.1-7.el8.x86_64                         407/1201 
  Reinstalling     : librepo-1.12.0-3.el8.x86_64                       408/1201 
  Reinstalling     : libdnf-0.55.0-7.el8.x86_64                        409/1201 
  Reinstalling     : PackageKit-1.1.12-6.el8.x86_64                    410/1201 
  Running scriptlet: PackageKit-1.1.12-6.el8.x86_64                    410/1201 
  Reinstalling     : python3-libdnf-0.55.0-7.el8.x86_64                411/1201 
  Reinstalling     : python3-hawkey-0.55.0-7.el8.x86_64                412/1201 
  Downgrading      : podman-catatonit-3.0.1-7.module+el8.4.0+556+40    413/1201 
  Downgrading      : podman-3.0.1-7.module+el8.4.0+556+40122d08.x86    414/1201 
  Reinstalling     : python3-gpg-1.13.1-7.el8.x86_64                   415/1201 
  Reinstalling     : rpm-build-libs-4.14.3-13.el8.x86_64               416/1201 
  Running scriptlet: rpm-build-libs-4.14.3-13.el8.x86_64               416/1201 
  Reinstalling     : python3-rpm-4.14.3-13.el8.x86_64                  417/1201 
  Reinstalling     : grub2-tools-extra-1:2.02-99.el8.x86_64            418/1201 
  Reinstalling     : dracut-squash-049-135.git20210121.el8.x86_64      419/1201 
  Reinstalling     : virt-what-1.18-6.el8.x86_64                       420/1201 
  Reinstalling     : sssd-client-2.4.0-9.el8.x86_64                    421/1201 
  Running scriptlet: sssd-client-2.4.0-9.el8.x86_64                    421/1201 
  Reinstalling     : sudo-1.8.29-7.el8.x86_64                          422/1201 
  Running scriptlet: sudo-1.8.29-7.el8.x86_64                          422/1201 
  Reinstalling     : cryptsetup-2.3.3-4.el8.x86_64                     423/1201 
  Reinstalling     : libluksmeta-9-4.el8.x86_64                        424/1201 
  Running scriptlet: libluksmeta-9-4.el8.x86_64                        424/1201 
  Reinstalling     : luksmeta-9-4.el8.x86_64                           425/1201 
  Reinstalling     : clevis-luks-15-1.el8.x86_64                       426/1201 
  Reinstalling     : rpm-plugin-systemd-inhibit-4.14.3-13.el8.x86_6    427/1201 
  Reinstalling     : sscg-2.3.3-14.el8.x86_64                          428/1201 
  Running scriptlet: cockpit-ws-238.2-1.el8.x86_64                     429/1201 
  Reinstalling     : cockpit-ws-238.2-1.el8.x86_64                     429/1201 
  Running scriptlet: cockpit-ws-238.2-1.el8.x86_64                     429/1201 
  Reinstalling     : bind-export-libs-32:9.11.26-4.el8_4.x86_64        430/1201 
  Running scriptlet: bind-export-libs-32:9.11.26-4.el8_4.x86_64        430/1201 
  Reinstalling     : isns-utils-libs-0.99-1.el8.x86_64                 431/1201 
  Running scriptlet: isns-utils-libs-0.99-1.el8.x86_64                 431/1201 
  Reinstalling     : iscsi-initiator-utils-iscsiuio-6.2.1.2-1.gita8    432/1201 
  Running scriptlet: iscsi-initiator-utils-iscsiuio-6.2.1.2-1.gita8    432/1201 
  Reinstalling     : iscsi-initiator-utils-6.2.1.2-1.gita8fcb37.el8    433/1201 
  Running scriptlet: iscsi-initiator-utils-6.2.1.2-1.gita8fcb37.el8    433/1201 
  Reinstalling     : device-mapper-multipath-libs-0.8.4-10.el8.x86_    434/1201 
  Running scriptlet: device-mapper-multipath-libs-0.8.4-10.el8.x86_    434/1201 
  Reinstalling     : device-mapper-multipath-0.8.4-10.el8.x86_64       435/1201 
  Running scriptlet: device-mapper-multipath-0.8.4-10.el8.x86_64       435/1201 
  Upgrading        : e2fsprogs-1.45.6-1.el8.1.x86_64                   436/1201 
  Downgrading      : dhcp-libs-12:4.3.6-44.el8_4.1.x86_64              437/1201 
  Reinstalling     : libatasmart-0.19-14.el8.x86_64                    438/1201 
  Running scriptlet: libatasmart-0.19-14.el8.x86_64                    438/1201 
  Reinstalling     : plymouth-core-libs-0.9.4-9.20200615git1e36e30.    439/1201 
  Running scriptlet: plymouth-core-libs-0.9.4-9.20200615git1e36e30.    439/1201 
  Reinstalling     : plymouth-scripts-0.9.4-9.20200615git1e36e30.el    440/1201 
  Reinstalling     : plymouth-0.9.4-9.20200615git1e36e30.el8.x86_64    441/1201 
  Reinstalling     : python3-systemd-234-8.el8.x86_64                  442/1201 
  Reinstalling     : nss-3.53.1-17.el8_3.x86_64                        443/1201 
  Reinstalling     : nss-sysinit-3.53.1-17.el8_3.x86_64                444/1201 
  Reinstalling     : libfprint-1.90.7-1.el8.x86_64                     445/1201 
  Reinstalling     : fprintd-1.90.9-2.el8.x86_64                       446/1201 
  Reinstalling     : volume_key-libs-0.3.11-5.el8.x86_64               447/1201 
  Reinstalling     : libblockdev-crypto-2.24-5.el8.x86_64              448/1201 
  Reinstalling     : udisks2-2.9.0-6.el8.x86_64                        449/1201 
  Running scriptlet: udisks2-2.9.0-6.el8.x86_64                        449/1201 
  Reinstalling     : udisks2-iscsi-2.9.0-6.el8.x86_64                  450/1201 
  Reinstalling     : udisks2-lvm2-2.9.0-6.el8.x86_64                   451/1201 
  Reinstalling     : binutils-2.30-93.el8.x86_64                       452/1201 
  Running scriptlet: binutils-2.30-93.el8.x86_64                       452/1201 
  Reinstalling     : teamd-1.31-2.el8.x86_64                           453/1201 
  Reinstalling     : NetworkManager-team-1:1.30.0-7.el8.x86_64         454/1201 
  Reinstalling     : libnfsidmap-1:2.3.3-41.el8.x86_64                 455/1201 
  Reinstalling     : sssd-nfs-idmap-2.4.0-9.el8.x86_64                 456/1201 
  Running scriptlet: sssd-common-2.4.0-9.el8.x86_64                    457/1201 
  Reinstalling     : sssd-common-2.4.0-9.el8.x86_64                    457/1201 
  Running scriptlet: sssd-common-2.4.0-9.el8.x86_64                    457/1201 
  Running scriptlet: sssd-krb5-common-2.4.0-9.el8.x86_64               458/1201 
  Reinstalling     : sssd-krb5-common-2.4.0-9.el8.x86_64               458/1201 
  Reinstalling     : sssd-common-pac-2.4.0-9.el8.x86_64                459/1201 
  Reinstalling     : sssd-krb5-2.4.0-9.el8.x86_64                      460/1201 
  Reinstalling     : sssd-ldap-2.4.0-9.el8.x86_64                      461/1201 
  Running scriptlet: sssd-proxy-2.4.0-9.el8.x86_64                     462/1201 
  Reinstalling     : sssd-proxy-2.4.0-9.el8.x86_64                     462/1201 
  Reinstalling     : python3-psutil-5.4.3-10.el8.x86_64                463/1201 
  Reinstalling     : python3-ptyprocess-0.5.2-4.el8.noarch             464/1201 
  Reinstalling     : python3-pexpect-4.3.1-3.el8.noarch                465/1201 
  Reinstalling     : sos-4.0-11.el8.noarch                             466/1201 
  Reinstalling     : python3-webencodings-0.5.1-6.el8.noarch           467/1201 
  Reinstalling     : python3-html5lib-1:0.999999999-6.el8.noarch       468/1201 
  Reinstalling     : python3-lxml-4.2.3-2.el8.x86_64                   469/1201 
  Reinstalling     : python3-libcomps-0.1.11-5.el8.x86_64              470/1201 
  Reinstalling     : python3-dnf-4.4.2-11.el8.noarch                   471/1201 
  Reinstalling     : dnf-4.4.2-11.el8.noarch                           472/1201 
  Running scriptlet: dnf-4.4.2-11.el8.noarch                           472/1201 
  Reinstalling     : kpatch-dnf-0.2-3.el8.noarch                       473/1201 
  Running scriptlet: kpatch-dnf-0.2-3.el8.noarch                       473/1201 
To enable automatic kpatch-patch subscription, run:
        $ dnf kpatch auto

  Reinstalling     : python3-dnf-plugins-core-4.0.18-4.el8.noarch      474/1201 
  Reinstalling     : python3-ply-3.9-9.el8.noarch                      475/1201 
  Reinstalling     : python3-bind-32:9.11.26-4.el8_4.noarch            476/1201 
  Reinstalling     : bind-utils-32:9.11.26-4.el8_4.x86_64              477/1201 
  Reinstalling     : sssd-ad-2.4.0-9.el8.x86_64                        478/1201 
  Running scriptlet: sssd-ipa-2.4.0-9.el8.x86_64                       479/1201 
  Reinstalling     : sssd-ipa-2.4.0-9.el8.x86_64                       479/1201 
  Reinstalling     : python3-pyyaml-3.12-12.el8.x86_64                 480/1201 
  Reinstalling     : python3-schedutils-0.6-6.el8.x86_64               481/1201 
  Reinstalling     : python3-setuptools-39.2.0-6.el8.noarch            482/1201 
  Reinstalling     : python3-sssdconfig-2.4.0-9.el8.noarch             483/1201 
  Reinstalling     : sssd-2.4.0-9.el8.x86_64                           484/1201 
  Reinstalling     : realmd-0.16.3-22.el8.x86_64                       485/1201 
  Reinstalling     : authselect-1.2.2-2.el8.x86_64                     486/1201 
  Reinstalling     : authselect-compat-1.2.2-2.el8.x86_64              487/1201 
  Reinstalling     : fprintd-pam-1.90.9-2.el8.x86_64                   488/1201 
  Reinstalling     : python3-syspurpose-1.28.13-2.el8.x86_64           489/1201 
  Upgrading        : kernel-tools-4.18.0-305.3.1.el8_4.x86_64          490/1201 
  Upgrading        : python3-perf-4.18.0-305.3.1.el8_4.x86_64          491/1201 
  Reinstalling     : vim-filesystem-2:8.0.1763-15.el8.noarch           492/1201 
  Reinstalling     : vim-common-2:8.0.1763-15.el8.x86_64               493/1201 
  Reinstalling     : tracer-common-0.7.5-2.el8.noarch                  494/1201 
  Reinstalling     : python3-tracer-0.7.5-2.el8.noarch                 495/1201 
  Reinstalling     : cockpit-packagekit-238.2-1.el8.noarch             496/1201 
  Reinstalling     : man-pages-overrides-8.3.0.2-2.el8.noarch          497/1201 
  Reinstalling     : libX11-common-1.6.8-4.el8.noarch                  498/1201 
  Reinstalling     : libX11-1.6.8-4.el8.x86_64                         499/1201 
  Reinstalling     : libXext-1.3.4-1.el8.x86_64                        500/1201 
  Reinstalling     : libXrender-0.9.10-7.el8.x86_64                    501/1201 
  Reinstalling     : cairo-1.15.12-3.el8.x86_64                        502/1201 
  Reinstalling     : cairo-gobject-1.15.12-3.el8.x86_64                503/1201 
  Reinstalling     : python3-cairo-1.16.3-6.el8.x86_64                 504/1201 
  Reinstalling     : python3-gobject-3.28.3-2.el8.x86_64               505/1201 
  Reinstalling     : setroubleshoot-plugins-3.3.13-1.el8.noarch        506/1201 
  Running scriptlet: setroubleshoot-server-3.3.24-3.el8.x86_64         507/1201 
  Reinstalling     : setroubleshoot-server-3.3.24-3.el8.x86_64         507/1201 
  Running scriptlet: setroubleshoot-server-3.3.24-3.el8.x86_64         507/1201 
  Downgrading      : dhcp-common-12:4.3.6-44.el8_4.1.noarch            508/1201 
  Downgrading      : dhcp-client-12:4.3.6-44.el8_4.1.x86_64            509/1201 
  Reinstalling     : dracut-network-049-135.git20210121.el8.x86_64     510/1201 
  Reinstalling     : kexec-tools-2.0.20-46.el8.x86_64                  511/1201 
  Running scriptlet: kexec-tools-2.0.20-46.el8.x86_64                  511/1201 
  Reinstalling     : cockpit-system-238.2-1.el8.noarch                 512/1201 
  Reinstalling     : cockpit-storaged-238.2-1.el8.noarch               513/1201 
  Reinstalling     : cockpit-238.2-1.el8.x86_64                        514/1201 
  Running scriptlet: chrony-3.5-2.el8.x86_64                           515/1201 
  Reinstalling     : chrony-3.5-2.el8.x86_64                           515/1201 
  Running scriptlet: chrony-3.5-2.el8.x86_64                           515/1201 
  Reinstalling     : man-pages-4.15-6.el8.x86_64                       516/1201 
  Reinstalling     : vim-enhanced-2:8.0.1763-15.el8.x86_64             517/1201 
  Reinstalling     : tuned-2.15.0-2.el8.noarch                         518/1201 
  Running scriptlet: tuned-2.15.0-2.el8.noarch                         518/1201 
  Reinstalling     : vdo-6.2.4.14-14.el8.x86_64                        519/1201 
  Running scriptlet: vdo-6.2.4.14-14.el8.x86_64                        519/1201 
  Reinstalling     : dnf-plugins-core-4.0.18-4.el8.noarch              520/1201 
  Reinstalling     : kpatch-0.9.2-3.el8.noarch                         521/1201 
  Reinstalling     : yum-4.4.2-11.el8.noarch                           522/1201 
  Reinstalling     : sssd-kcm-2.4.0-9.el8.x86_64                       523/1201 
  Running scriptlet: sssd-kcm-2.4.0-9.el8.x86_64                       523/1201 
  Reinstalling     : grub2-pc-1:2.02-99.el8.x86_64                     524/1201 
  Downgrading      : cockpit-podman-29-2.module+el8.4.0+556+40122d0    525/1201 
  Downgrading      : buildah-1.19.7-2.module+el8.4.0+556+40122d08.x    526/1201 
  Reinstalling     : wget-1.19.5-10.el8.x86_64                         527/1201 
  Running scriptlet: wget-1.19.5-10.el8.x86_64                         527/1201 
  Reinstalling     : firewalld-0.8.2-6.el8.noarch                      528/1201 
  Running scriptlet: firewalld-0.8.2-6.el8.noarch                      528/1201 
  Reinstalling     : pinfo-0.6.10-18.el8.x86_64                        529/1201 
  Running scriptlet: pinfo-0.6.10-18.el8.x86_64                        529/1201 
  Upgrading        : rsyslog-relp-8.1911.0-7.el8.1.x86_64              530/1201 
  Installing       : kernel-4.18.0-305.3.1.el8_4.x86_64                531/1201 
  Reinstalling     : xfsdump-3.1.8-2.el8.x86_64                        532/1201 
  Reinstalling     : openssh-clients-8.0p1-6.el8_4.2.x86_64            533/1201 
  Running scriptlet: openssh-server-8.0p1-6.el8_4.2.x86_64             534/1201 
  Reinstalling     : openssh-server-8.0p1-6.el8_4.2.x86_64             534/1201 
  Running scriptlet: openssh-server-8.0p1-6.el8_4.2.x86_64             534/1201 
  Reinstalling     : passwd-0.80-3.el8.x86_64                          535/1201 
  Reinstalling     : util-linux-user-2.32.1-27.el8.x86_64              536/1201 
  Reinstalling     : NetworkManager-tui-1:1.30.0-7.el8.x86_64          537/1201 
  Upgrading        : rsyslog-gnutls-8.1911.0-7.el8.1.x86_64            538/1201 
  Upgrading        : rsyslog-gssapi-8.1911.0-7.el8.1.x86_64            539/1201 
  Reinstalling     : iptstate-2.2.6-6.el8.x86_64                       540/1201 
  Reinstalling     : usbutils-010-3.el8.x86_64                         541/1201 
  Reinstalling     : bolt-0.9.1-1.el8.x86_64                           542/1201 
  Running scriptlet: bolt-0.9.1-1.el8.x86_64                           542/1201 
  Reinstalling     : at-3.1.20-11.el8.x86_64                           543/1201 
  Running scriptlet: at-3.1.20-11.el8.x86_64                           543/1201 
  Reinstalling     : mcelog-3:173-0.el8.x86_64                         544/1201 
  Running scriptlet: mcelog-3:173-0.el8.x86_64                         544/1201 
  Reinstalling     : microcode_ctl-4:20210216-1.20210525.1.el8_4.x8    545/1201 
  Running scriptlet: microcode_ctl-4:20210216-1.20210525.1.el8_4.x8    545/1201 
  Running scriptlet: mlocate-0.26-20.el8.x86_64                        546/1201 
  Reinstalling     : mlocate-0.26-20.el8.x86_64                        546/1201 
  Running scriptlet: mlocate-0.26-20.el8.x86_64                        546/1201 
  Reinstalling     : net-tools-2.0-0.52.20160912git.el8.x86_64         547/1201 
  Running scriptlet: net-tools-2.0-0.52.20160912git.el8.x86_64         547/1201 
  Reinstalling     : psacct-6.6.3-4.el8.x86_64                         548/1201 
  Running scriptlet: psacct-6.6.3-4.el8.x86_64                         548/1201 
  Running scriptlet: smartmontools-1:7.1-1.el8.x86_64                  549/1201 
  Reinstalling     : smartmontools-1:7.1-1.el8.x86_64                  549/1201 
  Running scriptlet: smartmontools-1:7.1-1.el8.x86_64                  549/1201 
  Reinstalling     : irqbalance-2:1.4.0-6.el8.x86_64                   550/1201 
  Running scriptlet: irqbalance-2:1.4.0-6.el8.x86_64                   550/1201 
  Reinstalling     : dracut-config-rescue-049-135.git20210121.el8.x    551/1201 
  Downgrading      : nvme-cli-1.12-3.el8.x86_64                        552/1201 
  Running scriptlet: nvme-cli-1.12-3.el8.x86_64                        552/1201 
  Reinstalling     : nmap-ncat-2:7.70-5.el8.x86_64                     553/1201 
  Running scriptlet: nmap-ncat-2:7.70-5.el8.x86_64                     553/1201 
  Running scriptlet: tcpdump-14:4.9.3-1.el8.x86_64                     554/1201 
  Reinstalling     : tcpdump-14:4.9.3-1.el8.x86_64                     554/1201 
  Reinstalling     : ledmon-0.95-1.el8.x86_64                          555/1201 
  Reinstalling     : prefixdevname-0.1.0-6.el8.x86_64                  556/1201 
  Running scriptlet: man-db-2.7.6.1-17.el8.x86_64                      557/1201 
  Reinstalling     : man-db-2.7.6.1-17.el8.x86_64                      557/1201 
  Running scriptlet: man-db-2.7.6.1-17.el8.x86_64                      557/1201 
  Reinstalling     : strace-5.7-2.el8.x86_64                           558/1201 
  Reinstalling     : lsof-4.93.2-1.el8.x86_64                          559/1201 
  Reinstalling     : quota-1:4.04-12.el8.x86_64                        560/1201 
  Reinstalling     : cyrus-sasl-plain-2.1.27-5.el8.x86_64              561/1201 
  Reinstalling     : blktrace-1.2.0-10.el8.x86_64                      562/1201 
  Reinstalling     : bash-completion-1:2.7-5.el8.noarch                563/1201 
  Reinstalling     : zip-3.0-23.el8.x86_64                             564/1201 
  Reinstalling     : sg3_utils-1.44-5.el8.x86_64                       565/1201 
  Reinstalling     : biosdevname-0.7.3-2.el8.x86_64                    566/1201 
  Reinstalling     : nano-2.9.8-1.el8.x86_64                           567/1201 
  Running scriptlet: nano-2.9.8-1.el8.x86_64                           567/1201 
  Reinstalling     : rsync-3.1.3-12.el8.x86_64                         568/1201 
  Reinstalling     : lshw-B.02.19.2-5.el8.x86_64                       569/1201 
  Upgrading        : bpftool-4.18.0-305.3.1.el8_4.x86_64               570/1201 
  Reinstalling     : bc-1.07.1-5.el8.x86_64                            571/1201 
  Running scriptlet: bc-1.07.1-5.el8.x86_64                            571/1201 
  Reinstalling     : ed-1.14.2-4.el8.x86_64                            572/1201 
  Running scriptlet: ed-1.14.2-4.el8.x86_64                            572/1201 
  Reinstalling     : time-1.9-3.el8.x86_64                             573/1201 
  Running scriptlet: time-1.9-3.el8.x86_64                             573/1201 
  Reinstalling     : iprutils-2.4.19-1.el8.x86_64                      574/1201 
  Running scriptlet: iprutils-2.4.19-1.el8.x86_64                      574/1201 
  Reinstalling     : hostname-3.20-6.el8.x86_64                        575/1201 
  Running scriptlet: hostname-3.20-6.el8.x86_64                        575/1201 
  Reinstalling     : mtr-2:0.92-3.el8.x86_64                           576/1201 
  Reinstalling     : dos2unix-7.4.0-3.el8.x86_64                       577/1201 
  Reinstalling     : libsysfs-2.1.0-24.el8.x86_64                      578/1201 
  Running scriptlet: libsysfs-2.1.0-24.el8.x86_64                      578/1201 
  Reinstalling     : lsscsi-0.32-2.el8.x86_64                          579/1201 
  Reinstalling     : symlinks-1.4-19.el8.x86_64                        580/1201 
  Reinstalling     : tree-1.7.0-15.el8.x86_64                          581/1201 
  Reinstalling     : langpacks-en-1.0-12.el8.noarch                    582/1201 
  Reinstalling     : words-3.0-28.el8.noarch                           583/1201 
  Reinstalling     : rootfiles-8.1-22.el8.noarch                       584/1201 
  Reinstalling     : mailcap-2.1.48-3.el8.noarch                       585/1201 
  Reinstalling     : libertas-usb8388-firmware-2:20201218-102.git05    586/1201 
  Reinstalling     : iwl7260-firmware-1:25.30.13.0-102.el8.1.noarch    587/1201 
  Reinstalling     : iwl6050-firmware-41.28.5.1-102.el8.1.noarch       588/1201 
  Reinstalling     : iwl6000g2b-firmware-18.168.6.1-102.el8.1.noarc    589/1201 
  Reinstalling     : iwl6000g2a-firmware-18.168.6.1-102.el8.1.noarc    590/1201 
  Reinstalling     : iwl6000-firmware-9.221.4.1-102.el8.1.noarch       591/1201 
  Reinstalling     : iwl5150-firmware-8.24.2.2-102.el8.1.noarch        592/1201 
  Reinstalling     : iwl5000-firmware-8.83.5.1_1-102.el8.1.noarch      593/1201 
  Reinstalling     : iwl3160-firmware-1:25.30.13.0-102.el8.1.noarch    594/1201 
  Reinstalling     : iwl2030-firmware-18.168.6.1-102.el8.1.noarch      595/1201 
  Reinstalling     : iwl2000-firmware-18.168.6.1-102.el8.1.noarch      596/1201 
  Reinstalling     : iwl135-firmware-18.168.6.1-102.el8.1.noarch       597/1201 
  Reinstalling     : iwl105-firmware-18.168.6.1-102.el8.1.noarch       598/1201 
  Reinstalling     : iwl1000-firmware-1:39.31.5.1-102.el8.1.noarch     599/1201 
  Reinstalling     : iwl100-firmware-39.31.5.1-102.el8.1.noarch        600/1201 
  Reinstalling     : alsa-sof-firmware-1.6.1-2.el8.noarch              601/1201 
  Reinstalling     : NetworkManager-config-server-1:1.30.0-7.el8.no    602/1201 
  Running scriptlet: sssd-kcm-2.4.0-9.el8.x86_64                       603/1201 
  Cleanup          : sssd-kcm-2.4.0-9.el8.x86_64                       603/1201 
  Running scriptlet: sssd-kcm-2.4.0-9.el8.x86_64                       603/1201 
  Running scriptlet: openssh-server-8.0p1-6.el8_4.2.x86_64             604/1201 
  Cleanup          : openssh-server-8.0p1-6.el8_4.2.x86_64             604/1201 
  Running scriptlet: openssh-server-8.0p1-6.el8_4.2.x86_64             604/1201 
  Cleanup          : NetworkManager-tui-1:1.30.0-7.el8.x86_64          605/1201 
  Cleanup          : python3-libstoragemgmt-clibs-1.8.7-1.el8.x86_6    606/1201 
  Running scriptlet: libstoragemgmt-1.8.7-1.el8.x86_64                 607/1201 
  Cleanup          : libstoragemgmt-1.8.7-1.el8.x86_64                 607/1201 
  Running scriptlet: libstoragemgmt-1.8.7-1.el8.x86_64                 607/1201 
  Cleanup          : python3-libstoragemgmt-1.8.7-1.el8.noarch         608/1201 
  Running scriptlet: vdo-6.2.4.14-14.el8.x86_64                        609/1201 
  Cleanup          : vdo-6.2.4.14-14.el8.x86_64                        609/1201 
  Running scriptlet: vdo-6.2.4.14-14.el8.x86_64                        609/1201 
  Running scriptlet: chrony-3.5-2.el8.x86_64                           610/1201 
  Cleanup          : chrony-3.5-2.el8.x86_64                           610/1201 
  Running scriptlet: chrony-3.5-2.el8.x86_64                           610/1201 
  Cleanup          : openssh-clients-8.0p1-6.el8_4.2.x86_64            611/1201 
  Running scriptlet: tuned-2.15.0-2.el8.noarch                         612/1201 
  Cleanup          : tuned-2.15.0-2.el8.noarch                         612/1201 
  Running scriptlet: tuned-2.15.0-2.el8.noarch                         612/1201 
  Running scriptlet: smartmontools-1:7.1-1.el8.x86_64                  613/1201 
  Cleanup          : smartmontools-1:7.1-1.el8.x86_64                  613/1201 
  Running scriptlet: smartmontools-1:7.1-1.el8.x86_64                  613/1201 
  Running scriptlet: wget-1.19.5-10.el8.x86_64                         614/1201 
  Cleanup          : wget-1.19.5-10.el8.x86_64                         614/1201 
  Cleanup          : kernel-tools-4.18.0-305.3.1.el8.x86_64            615/1201 
  Cleanup          : openssh-8.0p1-6.el8_4.2.x86_64                    616/1201 
  Cleanup          : crontabs-1.11-17.20190603git.el8.noarch           617/1201 
  Running scriptlet: cronie-1.5.2-4.el8.x86_64                         618/1201 
  Cleanup          : cronie-1.5.2-4.el8.x86_64                         618/1201 
  Running scriptlet: cronie-1.5.2-4.el8.x86_64                         618/1201 
  Cleanup          : cronie-anacron-1.5.2-4.el8.x86_64                 619/1201 
  Cleanup          : vim-enhanced-2:8.0.1763-15.el8.x86_64             620/1201 
  Cleanup          : buildah-1.19.7-2.module_el8.4.0+830+8027e1c4.x    621/1201 
  Running scriptlet: microcode_ctl-4:20210216-1.20210525.1.el8_4.x8    622/1201 
  Cleanup          : microcode_ctl-4:20210216-1.20210525.1.el8_4.x8    622/1201 
  Running scriptlet: microcode_ctl-4:20210216-1.20210525.1.el8_4.x8    622/1201 
  Running scriptlet: firewalld-0.8.2-6.el8.noarch                      623/1201 
  Cleanup          : firewalld-0.8.2-6.el8.noarch                      623/1201 
  Running scriptlet: firewalld-0.8.2-6.el8.noarch                      623/1201 
  Cleanup          : grub2-pc-1:2.02-99.el8.x86_64                     624/1201 
  Cleanup          : realmd-0.16.3-22.el8.x86_64                       625/1201 
  Running scriptlet: authselect-1.2.2-2.el8.x86_64                     626/1201 
  Cleanup          : authselect-1.2.2-2.el8.x86_64                     626/1201 
  Cleanup          : fprintd-pam-1.90.9-2.el8.x86_64                   627/1201 
  Running scriptlet: fprintd-pam-1.90.9-2.el8.x86_64                   627/1201 
  Cleanup          : authselect-compat-1.2.2-2.el8.x86_64              628/1201 
  Cleanup          : sssd-2.4.0-9.el8.x86_64                           629/1201 
  Cleanup          : python3-firewall-0.8.2-6.el8.noarch               630/1201 
  Running scriptlet: kmod-kvdo-6.2.4.26-77.el8.x86_64                  631/1201 
  Cleanup          : kmod-kvdo-6.2.4.26-77.el8.x86_64                  631/1201 
  Running scriptlet: kmod-kvdo-6.2.4.26-77.el8.x86_64                  631/1201 
  Running scriptlet: iptables-ebtables-1.8.4-17.el8.x86_64             632/1201 
  Cleanup          : iptables-ebtables-1.8.4-17.el8.x86_64             632/1201 
  Running scriptlet: iptables-ebtables-1.8.4-17.el8.x86_64             632/1201 
  Cleanup          : kpatch-0.9.2-3.el8.noarch                         633/1201 
  Cleanup          : cockpit-238.2-1.el8.x86_64                        634/1201 
  Cleanup          : cockpit-storaged-238.2-1.el8.noarch               635/1201 
  Cleanup          : cockpit-system-238.2-1.el8.noarch                 636/1201 
  Cleanup          : sos-4.0-11.el8.noarch                             637/1201 
  Cleanup          : clevis-luks-15-1.el8.x86_64                       638/1201 
  Cleanup          : kpatch-dnf-0.2-3.el8.noarch                       639/1201 
  Cleanup          : usb_modeswitch-data-20191128-1.el8.noarch         640/1201 
  Running scriptlet: usb_modeswitch-data-20191128-1.el8.noarch         640/1201 
  Cleanup          : cockpit-packagekit-238.2-1.el8.noarch             641/1201 
  Cleanup          : python3-tracer-0.7.5-2.el8.noarch                 642/1201 
  Cleanup          : python3-linux-procfs-0.6.3-1.el8.noarch           643/1201 
  Cleanup          : python3-pyudev-0.21.0-7.el8.noarch                644/1201 
  Cleanup          : python3-setuptools-39.2.0-6.el8.noarch            645/1201 
  Cleanup          : python3-pexpect-4.3.1-3.el8.noarch                646/1201 
  Cleanup          : python3-nftables-1:0.9.3-18.el8.x86_64            647/1201 
  Cleanup          : python3-configobj-5.0.6-11.el8.noarch             648/1201 
  Cleanup          : python3-syspurpose-1.28.13-2.el8.x86_64           649/1201 
  Cleanup          : dracut-config-rescue-049-135.git20210121.el8.x    650/1201 
  Cleanup          : bash-completion-1:2.7-5.el8.noarch                651/1201 
  Cleanup          : pkgconf-pkg-config-1.4.2-1.el8.x86_64             652/1201 
  Cleanup          : cockpit-podman-29-2.module_el8.4.0+781+acf4c33    653/1201 
  Cleanup          : sssd-ipa-2.4.0-9.el8.x86_64                       654/1201 
  Cleanup          : sssd-ad-2.4.0-9.el8.x86_64                        655/1201 
  Cleanup          : libsmbclient-4.13.3-3.el8.x86_64                  656/1201 
  Running scriptlet: cockpit-ws-238.2-1.el8.x86_64                     657/1201 
  Cleanup          : cockpit-ws-238.2-1.el8.x86_64                     657/1201 
  Running scriptlet: cockpit-ws-238.2-1.el8.x86_64                     657/1201 
  Running scriptlet: kexec-tools-2.0.20-46.el8.x86_64                  658/1201 
  Cleanup          : kexec-tools-2.0.20-46.el8.x86_64                  658/1201 
  Running scriptlet: kexec-tools-2.0.20-46.el8.x86_64                  658/1201 
  Cleanup          : sssd-common-pac-2.4.0-9.el8.x86_64                659/1201 
  Running scriptlet: libwbclient-4.13.3-3.el8.x86_64                   660/1201 
  Cleanup          : libwbclient-4.13.3-3.el8.x86_64                   660/1201 
  Cleanup          : samba-client-libs-4.13.3-3.el8.x86_64             661/1201 
  Cleanup          : samba-common-libs-4.13.3-3.el8.x86_64             662/1201 
  Cleanup          : python3-lxml-4.2.3-2.el8.x86_64                   663/1201 
  Running scriptlet: device-mapper-multipath-0.8.4-10.el8.x86_64       664/1201 
  Cleanup          : device-mapper-multipath-0.8.4-10.el8.x86_64       664/1201 
  Running scriptlet: device-mapper-multipath-0.8.4-10.el8.x86_64       664/1201 
  Cleanup          : sssd-ldap-2.4.0-9.el8.x86_64                      665/1201 
  Cleanup          : sssd-proxy-2.4.0-9.el8.x86_64                     666/1201 
  Running scriptlet: binutils-2.30-93.el8.x86_64                       667/1201 
  Cleanup          : binutils-2.30-93.el8.x86_64                       667/1201 
  Running scriptlet: binutils-2.30-93.el8.x86_64                       667/1201 
  Cleanup          : device-mapper-multipath-libs-0.8.4-10.el8.x86_    668/1201 
  Running scriptlet: device-mapper-multipath-libs-0.8.4-10.el8.x86_    668/1201 
  Cleanup          : bind-utils-32:9.11.26-4.el8_4.x86_64              669/1201 
  Cleanup          : podman-3.0.1-7.module_el8.4.0+830+8027e1c4.x86    670/1201 
  Cleanup          : PackageKit-1.1.12-6.el8.x86_64                    671/1201 
  Cleanup          : sudo-1.8.29-7.el8.x86_64                          672/1201 
  Cleanup          : sssd-krb5-2.4.0-9.el8.x86_64                      673/1201 
  Cleanup          : cups-libs-1:2.2.6-38.el8.x86_64                   674/1201 
  Cleanup          : cockpit-bridge-238.2-1.el8.x86_64                 675/1201 
  Cleanup          : libxslt-1.1.32-6.el8.x86_64                       676/1201 
  Cleanup          : bind-libs-32:9.11.26-4.el8_4.x86_64               677/1201 
  Cleanup          : bind-libs-lite-32:9.11.26-4.el8_4.x86_64          678/1201 
  Cleanup          : cryptsetup-2.3.3-4.el8.x86_64                     679/1201 
  Cleanup          : sssd-krb5-common-2.4.0-9.el8.x86_64               680/1201 
  Running scriptlet: sssd-common-2.4.0-9.el8.x86_64                    681/1201 
  Cleanup          : sssd-common-2.4.0-9.el8.x86_64                    681/1201 
  Running scriptlet: sssd-common-2.4.0-9.el8.x86_64                    681/1201 
  Running scriptlet: sssd-client-2.4.0-9.el8.x86_64                    682/1201 
  Cleanup          : sssd-client-2.4.0-9.el8.x86_64                    682/1201 
  Running scriptlet: sssd-client-2.4.0-9.el8.x86_64                    682/1201 
  Cleanup          : clevis-15-1.el8.x86_64                            683/1201 
  Running scriptlet: nftables-1:0.9.3-18.el8.x86_64                    684/1201 
  Cleanup          : nftables-1:0.9.3-18.el8.x86_64                    684/1201 
  Running scriptlet: nftables-1:0.9.3-18.el8.x86_64                    684/1201 
  Cleanup          : libicu-60.3-2.el8_1.x86_64                        685/1201 
  Running scriptlet: libicu-60.3-2.el8_1.x86_64                        685/1201 
  Cleanup          : xfsdump-3.1.8-2.el8.x86_64                        686/1201 
  Cleanup          : adcli-0.8.2-9.el8.x86_64                          687/1201 
  Running scriptlet: adcli-0.8.2-9.el8.x86_64                          687/1201 
  Cleanup          : bpftool-4.18.0-305.3.1.el8.x86_64                 688/1201 
  Cleanup          : prefixdevname-0.1.0-6.el8.x86_64                  689/1201 
  Running scriptlet: bolt-0.9.1-1.el8.x86_64                           690/1201 
  Cleanup          : bolt-0.9.1-1.el8.x86_64                           690/1201 
  Running scriptlet: bolt-0.9.1-1.el8.x86_64                           690/1201 
  Running scriptlet: at-3.1.20-11.el8.x86_64                           691/1201 
  Cleanup          : at-3.1.20-11.el8.x86_64                           691/1201 
  Running scriptlet: at-3.1.20-11.el8.x86_64                           691/1201 
  Cleanup          : nmap-ncat-2:7.70-5.el8.x86_64                     692/1201 
  Running scriptlet: nmap-ncat-2:7.70-5.el8.x86_64                     692/1201 
  Cleanup          : libldb-2.2.0-2.el8.x86_64                         693/1201 
  Cleanup          : libappstream-glib-0.7.14-3.el8.x86_64             694/1201 
  Cleanup          : gdk-pixbuf2-2.36.12-5.el8.x86_64                  695/1201 
  Running scriptlet: gdk-pixbuf2-2.36.12-5.el8.x86_64                  695/1201 
  Cleanup          : passwd-0.80-3.el8.x86_64                          696/1201 
  Cleanup          : man-db-2.7.6.1-17.el8.x86_64                      697/1201 
  Cleanup          : lshw-B.02.19.2-5.el8.x86_64                       698/1201 
  Cleanup          : iptstate-2.2.6-6.el8.x86_64                       699/1201 
  Cleanup          : iptables-1.8.4-17.el8.x86_64                      700/1201 
  Running scriptlet: iptables-1.8.4-17.el8.x86_64                      700/1201 
  Running scriptlet: psacct-6.6.3-4.el8.x86_64                         701/1201 
  Cleanup          : psacct-6.6.3-4.el8.x86_64                         701/1201 
  Running scriptlet: psacct-6.6.3-4.el8.x86_64                         701/1201 
  Running scriptlet: irqbalance-2:1.4.0-6.el8.x86_64                   702/1201 
  Cleanup          : irqbalance-2:1.4.0-6.el8.x86_64                   702/1201 
  Running scriptlet: irqbalance-2:1.4.0-6.el8.x86_64                   702/1201 
  Cleanup          : libini_config-1.3.1-39.el8.x86_64                 703/1201 
  Cleanup          : blktrace-1.2.0-10.el8.x86_64                      704/1201 
  Cleanup          : oddjob-mkhomedir-0.34.7-1.el8.x86_64              705/1201 
  Running scriptlet: oddjob-0.34.7-1.el8.x86_64                        706/1201 
  Cleanup          : oddjob-0.34.7-1.el8.x86_64                        706/1201 
  Running scriptlet: oddjob-0.34.7-1.el8.x86_64                        706/1201 
  Running scriptlet: mlocate-0.26-20.el8.x86_64                        707/1201 
  Cleanup          : mlocate-0.26-20.el8.x86_64                        707/1201 
  Running scriptlet: mlocate-0.26-20.el8.x86_64                        707/1201 
  Running scriptlet: iprutils-2.4.19-1.el8.x86_64                      708/1201 
  Cleanup          : iprutils-2.4.19-1.el8.x86_64                      708/1201 
  Cleanup          : groff-base-1.22.3-18.el8.x86_64                   709/1201 
  Cleanup          : runc-1.0.0-73.rc93.module_el8.4.0+830+8027e1c4    710/1201 
  Cleanup          : criu-3.15-1.module_el8.4.0+641+6116a774.x86_64    711/1201 
  Running scriptlet: tar-2:1.30-5.el8.x86_64                           712/1201 
  Cleanup          : tar-2:1.30-5.el8.x86_64                           712/1201 
  Cleanup          : authselect-libs-1.2.2-2.el8.x86_64                713/1201 
  Cleanup          : grub2-tools-extra-1:2.02-99.el8.x86_64            714/1201 
  Cleanup          : util-linux-user-2.32.1-27.el8.x86_64              715/1201 
  Cleanup          : libuser-0.62-23.el8.x86_64                        716/1201 
  Running scriptlet: libuser-0.62-23.el8.x86_64                        716/1201 
  Cleanup          : sg3_utils-1.44-5.el8.x86_64                       717/1201 
  Cleanup          : ledmon-0.95-1.el8.x86_64                          718/1201 
  Cleanup          : plymouth-0.9.4-9.20200615git1e36e30.el8.x86_64    719/1201 
  Running scriptlet: plymouth-0.9.4-9.20200615git1e36e30.el8.x86_64    719/1201 
  Cleanup          : plymouth-core-libs-0.9.4-9.20200615git1e36e30.    720/1201 
  Running scriptlet: plymouth-core-libs-0.9.4-9.20200615git1e36e30.    720/1201 
  Cleanup          : jose-10-2.el8.x86_64                              721/1201 
  Cleanup          : libjose-10-2.el8.x86_64                           722/1201 
  Running scriptlet: libjose-10-2.el8.x86_64                           722/1201 
  Cleanup          : conmon-2:2.0.26-3.module_el8.4.0+830+8027e1c4.    723/1201 
  Cleanup          : python3-perf-4.18.0-305.3.1.el8.x86_64            724/1201 
  Cleanup          : strace-5.7-2.el8.x86_64                           725/1201 
  Cleanup          : rsync-3.1.3-12.el8.x86_64                         726/1201 
  Cleanup          : libsoup-2.62.3-2.el8.x86_64                       727/1201 
  Cleanup          : libsss_nss_idmap-2.4.0-9.el8.x86_64               728/1201 
  Running scriptlet: libsss_nss_idmap-2.4.0-9.el8.x86_64               728/1201 
  Cleanup          : PackageKit-glib-1.1.12-6.el8.x86_64               729/1201 
  Cleanup          : NetworkManager-team-1:1.30.0-7.el8.x86_64         730/1201 
  Cleanup          : teamd-1.31-2.el8.x86_64                           731/1201 
  Cleanup          : libteam-1.31-2.el8.x86_64                         732/1201 
  Running scriptlet: libteam-1.31-2.el8.x86_64                         732/1201 
  Cleanup          : libnl3-cli-3.5.0-1.el8.x86_64                     733/1201 
  Running scriptlet: libnl3-cli-3.5.0-1.el8.x86_64                     733/1201 
  Cleanup          : libconfig-1.5-9.el8.x86_64                        734/1201 
  Running scriptlet: nano-2.9.8-1.el8.x86_64                           735/1201 
  Cleanup          : nano-2.9.8-1.el8.x86_64                           735/1201 
  Running scriptlet: mcelog-3:173-0.el8.x86_64                         736/1201 
  Cleanup          : mcelog-3:173-0.el8.x86_64                         736/1201 
  Running scriptlet: mcelog-3:173-0.el8.x86_64                         736/1201 
  Cleanup          : glib-networking-2.56.1-1.1.el8.x86_64             737/1201 
  Cleanup          : libproxy-0.4.15-5.2.el8.x86_64                    738/1201 
  Running scriptlet: libproxy-0.4.15-5.2.el8.x86_64                    738/1201 
  Cleanup          : libmodman-2.0.1-17.el8.x86_64                     739/1201 
  Running scriptlet: libmodman-2.0.1-17.el8.x86_64                     739/1201 
  Cleanup          : cyrus-sasl-gssapi-2.1.27-5.el8.x86_64             740/1201 
  Cleanup          : tpm2-tools-4.1.1-2.el8.x86_64                     741/1201 
  Cleanup          : libsss_certmap-2.4.0-9.el8.x86_64                 742/1201 
  Running scriptlet: libsss_certmap-2.4.0-9.el8.x86_64                 742/1201 
  Cleanup          : sscg-2.3.3-14.el8.x86_64                          743/1201 
  Cleanup          : fprintd-1.90.9-2.el8.x86_64                       744/1201 
  Cleanup          : libfprint-1.90.7-1.el8.x86_64                     745/1201 
  Running scriptlet: timedatex-0.5-3.el8.x86_64                        746/1201 
  Cleanup          : timedatex-0.5-3.el8.x86_64                        746/1201 
  Running scriptlet: timedatex-0.5-3.el8.x86_64                        746/1201 
  Cleanup          : libtevent-0.10.2-2.el8.x86_64                     747/1201 
  Cleanup          : vim-minimal-2:8.0.1763-15.el8.x86_64              748/1201 
  Cleanup          : udisks2-lvm2-2.9.0-6.el8.x86_64                   749/1201 
  Cleanup          : libblockdev-lvm-2.24-5.el8.x86_64                 750/1201 
  Running scriptlet: lvm2-8:2.03.11-5.el8.x86_64                       751/1201 
  Cleanup          : lvm2-8:2.03.11-5.el8.x86_64                       751/1201 
  Running scriptlet: lvm2-8:2.03.11-5.el8.x86_64                       751/1201 
  Cleanup          : lvm2-libs-8:2.03.11-5.el8.x86_64                  752/1201 
  Running scriptlet: device-mapper-event-8:1.02.175-5.el8.x86_64       753/1201 
  Cleanup          : device-mapper-event-8:1.02.175-5.el8.x86_64       753/1201 
  Cleanup          : device-mapper-persistent-data-0.8.5-4.el8.x86_    754/1201 
  Cleanup          : device-mapper-event-libs-8:1.02.175-5.el8.x86_    755/1201 
  Cleanup          : cyrus-sasl-plain-2.1.27-5.el8.x86_64              756/1201 
  Running scriptlet: bc-1.07.1-5.el8.x86_64                            757/1201 
  Cleanup          : bc-1.07.1-5.el8.x86_64                            757/1201 
  Running scriptlet: pinfo-0.6.10-18.el8.x86_64                        758/1201 
  Cleanup          : pinfo-0.6.10-18.el8.x86_64                        758/1201 
  Cleanup          : libtdb-1.4.3-1.el8.x86_64                         759/1201 
  Running scriptlet: libtdb-1.4.3-1.el8.x86_64                         759/1201 
  Cleanup          : avahi-libs-0.7-20.el8.x86_64                      760/1201 
  Cleanup          : userspace-rcu-0.10.1-4.el8.x86_64                 761/1201 
  Running scriptlet: userspace-rcu-0.10.1-4.el8.x86_64                 761/1201 
  Cleanup          : python3-psutil-5.4.3-10.el8.x86_64                762/1201 
  Cleanup          : udisks2-iscsi-2.9.0-6.el8.x86_64                  763/1201 
  Running scriptlet: udisks2-2.9.0-6.el8.x86_64                        764/1201 
  Cleanup          : udisks2-2.9.0-6.el8.x86_64                        764/1201 
  Running scriptlet: udisks2-2.9.0-6.el8.x86_64                        764/1201 
  Running scriptlet: iscsi-initiator-utils-6.2.1.2-1.gita8fcb37.el8    765/1201 
  Cleanup          : iscsi-initiator-utils-6.2.1.2-1.gita8fcb37.el8    765/1201 
  Running scriptlet: iscsi-initiator-utils-6.2.1.2-1.gita8fcb37.el8    765/1201 
  Cleanup          : libblockdev-crypto-2.24-5.el8.x86_64              766/1201 
  Cleanup          : e2fsprogs-1.45.6-1.el8.x86_64                     767/1201 
  Cleanup          : libblockdev-fs-2.24-5.el8.x86_64                  768/1201 
  Cleanup          : volume_key-libs-0.3.11-5.el8.x86_64               769/1201 
  Cleanup          : nss-3.53.1-17.el8_3.x86_64                        770/1201 
  Cleanup          : nss-softokn-3.53.1-17.el8_3.x86_64                771/1201 
  Cleanup          : xfsprogs-5.0.0-8.el8.x86_64                       772/1201 
  Running scriptlet: xfsprogs-5.0.0-8.el8.x86_64                       772/1201 
  Running scriptlet: iscsi-initiator-utils-iscsiuio-6.2.1.2-1.gita8    773/1201 
  Cleanup          : iscsi-initiator-utils-iscsiuio-6.2.1.2-1.gita8    773/1201 
  Running scriptlet: iscsi-initiator-utils-iscsiuio-6.2.1.2-1.gita8    773/1201 
  Cleanup          : libblockdev-part-2.24-5.el8.x86_64                774/1201 
  Cleanup          : gdisk-1.0.3-6.el8.x86_64                          775/1201 
  Cleanup          : nss-sysinit-3.53.1-17.el8_3.x86_64                776/1201 
  Cleanup          : libblockdev-2.24-5.el8.x86_64                     777/1201 
  Cleanup          : fuse-libs-2.9.7-12.el8.x86_64                     778/1201 
  Running scriptlet: fuse-libs-2.9.7-12.el8.x86_64                     778/1201 
  Cleanup          : libblockdev-swap-2.24-5.el8.x86_64                779/1201 
  Cleanup          : libblockdev-mdraid-2.24-5.el8.x86_64              780/1201 
  Running scriptlet: mdadm-4.1-15.el8.x86_64                           781/1201 
  Cleanup          : mdadm-4.1-15.el8.x86_64                           781/1201 
  Running scriptlet: mdadm-4.1-15.el8.x86_64                           781/1201 
  Cleanup          : libss-1.45.6-1.el8.x86_64                         782/1201 
  Running scriptlet: libss-1.45.6-1.el8.x86_64                         782/1201 
  Cleanup          : libblockdev-loop-2.24-5.el8.x86_64                783/1201 
  Cleanup          : libblockdev-utils-2.24-5.el8.x86_64               784/1201 
  Running scriptlet: parted-3.2-38.el8.x86_64                          785/1201 
  Cleanup          : parted-3.2-38.el8.x86_64                          785/1201 
  Running scriptlet: parted-3.2-38.el8.x86_64                          785/1201 
  Cleanup          : nss-softokn-freebl-3.53.1-17.el8_3.x86_64         786/1201 
  Cleanup          : nss-util-3.53.1-17.el8_3.x86_64                   787/1201 
  Cleanup          : nspr-4.25.0-2.el8_2.x86_64                        788/1201 
  Running scriptlet: nspr-4.25.0-2.el8_2.x86_64                        788/1201 
  Cleanup          : usbutils-010-3.el8.x86_64                         789/1201 
  Cleanup          : mtr-2:0.92-3.el8.x86_64                           790/1201 
  Cleanup          : elfutils-debuginfod-client-0.182-3.el8.x86_64     791/1201 
  Running scriptlet: ed-1.14.2-4.el8.x86_64                            792/1201 
  Cleanup          : ed-1.14.2-4.el8.x86_64                            792/1201 
  Cleanup          : tcpdump-14:4.9.3-1.el8.x86_64                     793/1201 
  Cleanup          : numactl-libs-2.0.12-11.el8.x86_64                 794/1201 
  Running scriptlet: numactl-libs-2.0.12-11.el8.x86_64                 794/1201 
  Cleanup          : libnetfilter_conntrack-1.0.6-5.el8.x86_64         795/1201 
  Running scriptlet: libnetfilter_conntrack-1.0.6-5.el8.x86_64         795/1201 
  Cleanup          : jq-1.5-12.el8.x86_64                              796/1201 
  Cleanup          : ethtool-2:5.8-5.el8.x86_64                        797/1201 
  Cleanup          : newt-0.52.20-11.el8.x86_64                        798/1201 
  Cleanup          : slang-2.3.2-3.el8.x86_64                          799/1201 
  Cleanup          : quota-1:4.04-12.el8.x86_64                        800/1201 
  Cleanup          : e2fsprogs-libs-1.45.6-1.el8.x86_64                801/1201 
  Running scriptlet: e2fsprogs-libs-1.45.6-1.el8.x86_64                801/1201 
  Cleanup          : net-tools-2.0-0.52.20160912git.el8.x86_64         802/1201 
  Cleanup          : biosdevname-0.7.3-2.el8.x86_64                    803/1201 
  Cleanup          : nvme-cli-1.12-3.el8.0.1.x86_64                    804/1201 
  Cleanup          : container-selinux-2:2.162.0-1.module_el8.4.0+8    805/1201 
  Running scriptlet: container-selinux-2:2.162.0-1.module_el8.4.0+8    805/1201 
  Cleanup          : dracut-network-049-135.git20210121.el8.x86_64     806/1201 
  Cleanup          : dhcp-client-12:4.3.6-44.0.1.el8.x86_64            807/1201 
  Cleanup          : dhcp-libs-12:4.3.6-44.0.1.el8.x86_64              808/1201 
  Cleanup          : rpm-plugin-selinux-4.14.3-13.el8.x86_64           809/1201 
  Cleanup          : selinux-policy-targeted-3.14.3-67.el8.noarch      810/1201 
  Running scriptlet: selinux-policy-targeted-3.14.3-67.el8.noarch      810/1201 
  Cleanup          : selinux-policy-3.14.3-67.el8.noarch               811/1201 
  Running scriptlet: selinux-policy-3.14.3-67.el8.noarch               811/1201 
  Cleanup          : plymouth-scripts-0.9.4-9.20200615git1e36e30.el    812/1201 
  Cleanup          : python3-bind-32:9.11.26-4.el8_4.noarch            813/1201 
  Cleanup          : xdg-utils-1.1.2-5.el8.noarch                      814/1201 
  Cleanup          : samba-common-4.13.3-3.el8.noarch                  815/1201 
  Cleanup          : gsettings-desktop-schemas-3.32.0-5.el8.x86_64     816/1201 
  Cleanup          : containers-common-1:1.2.2-10.module_el8.4.0+83    817/1201 
  Cleanup          : python3-html5lib-1:0.999999999-6.el8.noarch       818/1201 
  Cleanup          : dracut-squash-049-135.git20210121.el8.x86_64      819/1201 
  Cleanup          : python3-webencodings-0.5.1-6.el8.noarch           820/1201 
  Cleanup          : dejavu-sans-mono-fonts-2.35-7.el8.noarch          821/1201 
  Cleanup          : dejavu-fonts-common-2.35-7.el8.noarch             822/1201 
  Cleanup          : python3-ply-3.9-9.el8.noarch                      823/1201 
  Cleanup          : python3-ptyprocess-0.5.2-4.el8.noarch             824/1201 
  Cleanup          : python3-sssdconfig-2.4.0-9.el8.noarch             825/1201 
  Cleanup          : grub2-pc-modules-1:2.02-99.el8.noarch             826/1201 
  Cleanup          : yum-4.4.2-11.el8.noarch                           827/1201 
  Running scriptlet: dnf-4.4.2-11.el8.noarch                           828/1201 
  Cleanup          : dnf-4.4.2-11.el8.noarch                           828/1201 
  Running scriptlet: dnf-4.4.2-11.el8.noarch                           828/1201 
  Cleanup          : man-pages-4.15-6.el8.x86_64                       829/1201 
  Cleanup          : dnf-plugins-core-4.0.18-4.el8.noarch              830/1201 
  Cleanup          : python3-dnf-plugins-core-4.0.18-4.el8.noarch      831/1201 
  Cleanup          : python3-dnf-4.4.2-11.el8.noarch                   832/1201 
  Cleanup          : python3-dateutil-1:2.6.1-6.el8.noarch             833/1201 
  Cleanup          : dnf-data-4.4.2-11.el8.noarch                      834/1201 
  Cleanup          : setroubleshoot-plugins-3.3.13-1.el8.noarch        835/1201 
  Cleanup          : langpacks-en-1.0-12.el8.noarch                    836/1201 
  Cleanup          : libreport-filesystem-2.9.5-15.el8.x86_64          837/1201 
  Cleanup          : man-pages-overrides-8.3.0.2-2.el8.noarch          838/1201 
  Cleanup          : bind-license-32:9.11.26-4.el8_4.noarch            839/1201 
  Cleanup          : dhcp-common-12:4.3.6-44.0.1.el8.noarch            840/1201 
  Cleanup          : quota-nls-1:4.04-12.el8.noarch                    841/1201 
  Cleanup          : podman-catatonit-3.0.1-7.module_el8.4.0+830+80    842/1201 
  Cleanup          : pkgconf-m4-1.4.2-1.el8.noarch                     843/1201 
  Cleanup          : tracer-common-0.7.5-2.el8.noarch                  844/1201 
  Cleanup          : firewalld-filesystem-0.8.2-6.el8.noarch           845/1201 
  Cleanup          : words-3.0-28.el8.noarch                           846/1201 
  Cleanup          : rootfiles-8.1-22.el8.noarch                       847/1201 
  Cleanup          : mailcap-2.1.48-3.el8.noarch                       848/1201 
  Cleanup          : linux-firmware-20201218-102.git05789708.el8.no    849/1201 
  Cleanup          : libertas-usb8388-firmware-2:20201218-102.git05    850/1201 
  Cleanup          : iwl7260-firmware-1:25.30.13.0-102.el8.1.noarch    851/1201 
  Cleanup          : iwl6050-firmware-41.28.5.1-102.el8.1.noarch       852/1201 
  Cleanup          : iwl6000g2b-firmware-18.168.6.1-102.el8.1.noarc    853/1201 
  Cleanup          : iwl6000g2a-firmware-18.168.6.1-102.el8.1.noarc    854/1201 
  Cleanup          : iwl6000-firmware-9.221.4.1-102.el8.1.noarch       855/1201 
  Cleanup          : iwl5150-firmware-8.24.2.2-102.el8.1.noarch        856/1201 
  Cleanup          : iwl5000-firmware-8.83.5.1_1-102.el8.1.noarch      857/1201 
  Cleanup          : iwl3160-firmware-1:25.30.13.0-102.el8.1.noarch    858/1201 
  Cleanup          : iwl2030-firmware-18.168.6.1-102.el8.1.noarch      859/1201 
  Cleanup          : iwl2000-firmware-18.168.6.1-102.el8.1.noarch      860/1201 
  Cleanup          : iwl135-firmware-18.168.6.1-102.el8.1.noarch       861/1201 
  Cleanup          : iwl105-firmware-18.168.6.1-102.el8.1.noarch       862/1201 
  Cleanup          : iwl1000-firmware-1:39.31.5.1-102.el8.1.noarch     863/1201 
  Cleanup          : iwl100-firmware-39.31.5.1-102.el8.1.noarch        864/1201 
  Cleanup          : alsa-sof-firmware-1.6.1-2.el8.noarch              865/1201 
  Cleanup          : NetworkManager-config-server-1:1.30.0-7.el8.no    866/1201 
  Running scriptlet: NetworkManager-1:1.30.0-7.el8.x86_64              867/1201 
  Cleanup          : NetworkManager-1:1.30.0-7.el8.x86_64              867/1201 
  Running scriptlet: NetworkManager-1:1.30.0-7.el8.x86_64              867/1201 
  Cleanup          : python3-hawkey-0.55.0-7.el8.x86_64                868/1201 
  Cleanup          : python3-libdnf-0.55.0-7.el8.x86_64                869/1201 
  Cleanup          : libdnf-0.55.0-7.el8.x86_64                        870/1201 
  Cleanup          : setroubleshoot-server-3.3.24-3.el8.x86_64         871/1201 
  Running scriptlet: setroubleshoot-server-3.3.24-3.el8.x86_64         871/1201 
  Cleanup          : python3-libxml2-2.9.7-9.el8.x86_64                872/1201 
  Running scriptlet: polkit-0.115-11.el8_4.1.x86_64                    873/1201 
  Cleanup          : polkit-0.115-11.el8_4.1.x86_64                    873/1201 
  Running scriptlet: polkit-0.115-11.el8_4.1.x86_64                    873/1201 
  Running scriptlet: audit-3.0-0.17.20191104git1c2f876.el8.x86_64      874/1201 
  Cleanup          : audit-3.0-0.17.20191104git1c2f876.el8.x86_64      874/1201 
  Running scriptlet: audit-3.0-0.17.20191104git1c2f876.el8.x86_64      874/1201 
  Cleanup          : python3-rpm-4.14.3-13.el8.x86_64                  875/1201 
  Cleanup          : rpm-build-libs-4.14.3-13.el8.x86_64               876/1201 
  Running scriptlet: rpm-build-libs-4.14.3-13.el8.x86_64               876/1201 
  Running scriptlet: initscripts-10.00.15-1.el8.x86_64                 877/1201 
  Cleanup          : initscripts-10.00.15-1.el8.x86_64                 877/1201 
  Running scriptlet: initscripts-10.00.15-1.el8.x86_64                 877/1201 
  Cleanup          : NetworkManager-libnm-1:1.30.0-7.el8.x86_64        878/1201 
  Running scriptlet: NetworkManager-libnm-1:1.30.0-7.el8.x86_64        878/1201 
  Cleanup          : mozjs60-60.9.0-4.el8.x86_64                       879/1201 
  Cleanup          : crun-0.18-2.module_el8.4.0+830+8027e1c4.x86_64    880/1201 
  Cleanup          : rpm-plugin-systemd-inhibit-4.14.3-13.el8.x86_6    881/1201 
  Running scriptlet: iputils-20180629-7.el8.x86_64                     882/1201 
  Cleanup          : iputils-20180629-7.el8.x86_64                     882/1201 
  Running scriptlet: iputils-20180629-7.el8.x86_64                     882/1201 
  Cleanup          : fuse-overlayfs-1.4.0-3.module_el8.4.0+830+8027    883/1201 
  Cleanup          : iproute-5.9.0-4.el8.x86_64                        884/1201 
  Cleanup          : librepo-1.12.0-3.el8.x86_64                       885/1201 
  Cleanup          : libsolv-0.7.16-2.el8.x86_64                       886/1201 
  Cleanup          : squashfs-tools-4.3-20.el8.x86_64                  887/1201 
  Cleanup          : bind-export-libs-32:9.11.26-4.el8_4.x86_64        888/1201 
  Running scriptlet: bind-export-libs-32:9.11.26-4.el8_4.x86_64        888/1201 
  Cleanup          : python3-systemd-234-8.el8.x86_64                  889/1201 
  Cleanup          : sqlite-3.26.0-13.el8.x86_64                       890/1201 
  Cleanup          : fuse3-libs-3.2.1-12.el8.x86_64                    891/1201 
  Running scriptlet: fuse3-libs-3.2.1-12.el8.x86_64                    891/1201 
  Cleanup          : slirp4netns-1.1.8-1.module_el8.4.0+641+6116a77    892/1201 
  Cleanup          : ima-evm-utils-1.3.2-12.el8.x86_64                 893/1201 
  Cleanup          : tpm2-tss-2.3.2-3.el8.x86_64                       894/1201 
  Running scriptlet: tpm2-tss-2.3.2-3.el8.x86_64                       894/1201 
  Cleanup          : python3-unbound-1.7.3-15.el8.x86_64               895/1201 
  Running scriptlet: unbound-libs-1.7.3-15.el8.x86_64                  896/1201 
  Cleanup          : unbound-libs-1.7.3-15.el8.x86_64                  896/1201 
  Running scriptlet: unbound-libs-1.7.3-15.el8.x86_64                  896/1201 
  Cleanup          : libevent-2.1.8-5.el8.x86_64                       897/1201 
  Cleanup          : libmodulemd-2.9.4-2.el8.x86_64                    898/1201 
  Cleanup          : python3-gpg-1.13.1-7.el8.x86_64                   899/1201 
  Cleanup          : gpgme-1.13.1-7.el8.x86_64                         900/1201 
  Cleanup          : gnupg2-2.2.20-2.el8.x86_64                        901/1201 
  Running scriptlet: pinentry-1.1.0-2.el8.x86_64                       902/1201 
  Cleanup          : pinentry-1.1.0-2.el8.x86_64                       902/1201 
  Cleanup          : gnupg2-smime-2.2.20-2.el8.x86_64                  903/1201 
  Cleanup          : libsecret-0.18.6-1.el8.x86_64                     904/1201 
  Cleanup          : python3-libcomps-0.1.11-5.el8.x86_64              905/1201 
  Cleanup          : libcomps-0.1.11-5.el8.x86_64                      906/1201 
  Cleanup          : python3-gobject-3.28.3-2.el8.x86_64               907/1201 
  Cleanup          : cairo-gobject-1.15.12-3.el8.x86_64                908/1201 
  Cleanup          : ipcalc-0.2.4-4.el8.x86_64                         909/1201 
  Cleanup          : libmaxminddb-1.2.0-10.el8.x86_64                  910/1201 
  Running scriptlet: libmaxminddb-1.2.0-10.el8.x86_64                  910/1201 
  Cleanup          : npth-1.5-4.el8.x86_64                             911/1201 
  Cleanup          : polkit-pkla-compat-0.1-12.el8.x86_64              912/1201 
  Cleanup          : polkit-libs-0.115-11.el8_4.1.x86_64               913/1201 
  Running scriptlet: polkit-libs-0.115-11.el8_4.1.x86_64               913/1201 
  Cleanup          : isns-utils-libs-0.99-1.el8.x86_64                 914/1201 
  Running scriptlet: isns-utils-libs-0.99-1.el8.x86_64                 914/1201 
  Cleanup          : libatasmart-0.19-14.el8.x86_64                    915/1201 
  Running scriptlet: libatasmart-0.19-14.el8.x86_64                    915/1201 
  Cleanup          : libnftnl-1.1.5-4.el8.x86_64                       916/1201 
  Running scriptlet: libnftnl-1.1.5-4.el8.x86_64                       916/1201 
  Cleanup          : libsss_idmap-2.4.0-9.el8.x86_64                   917/1201 
  Running scriptlet: libsss_idmap-2.4.0-9.el8.x86_64                   917/1201 
  Cleanup          : c-ares-1.13.0-5.el8.x86_64                        918/1201 
  Running scriptlet: c-ares-1.13.0-5.el8.x86_64                        918/1201 
  Cleanup          : libsss_sudo-2.4.0-9.el8.x86_64                    919/1201 
  Running scriptlet: libsss_sudo-2.4.0-9.el8.x86_64                    919/1201 
  Cleanup          : snappy-1.1.8-3.el8.x86_64                         920/1201 
  Cleanup          : python3-schedutils-0.6-6.el8.x86_64               921/1201 
  Cleanup          : rsyslog-gssapi-8.1911.0-7.el8.x86_64              922/1201 
  Cleanup          : libbytesize-1.4-3.el8.x86_64                      923/1201 
  Cleanup          : libgudev-232-4.el8.x86_64                         924/1201 
  Cleanup          : sg3_utils-libs-1.44-5.el8.x86_64                  925/1201 
  Running scriptlet: sg3_utils-libs-1.44-5.el8.x86_64                  925/1201 
  Cleanup          : psmisc-23.1-5.el8.x86_64                          926/1201 
  Cleanup          : less-530-1.el8.x86_64                             927/1201 
  Cleanup          : libpipeline-1.5.0-2.el8.x86_64                    928/1201 
  Running scriptlet: libpipeline-1.5.0-2.el8.x86_64                    928/1201 
  Cleanup          : lmdb-libs-0.9.24-1.el8.x86_64                     929/1201 
  Cleanup          : attr-2.4.48-3.el8.x86_64                          930/1201 
  Cleanup          : sssd-nfs-idmap-2.4.0-9.el8.x86_64                 931/1201 
  Cleanup          : libnfsidmap-1:2.3.3-41.el8.x86_64                 932/1201 
  Cleanup          : fstrm-0.6.0-3.el8.1.x86_64                        933/1201 
  Cleanup          : containernetworking-plugins-0.9.1-1.module_el8    934/1201 
  Cleanup          : usb_modeswitch-2.5.2-1.el8.x86_64                 935/1201 
  Cleanup          : jimtcl-0.77-6.el8.x86_64                          936/1201 
  Running scriptlet: jimtcl-0.77-6.el8.x86_64                          936/1201 
  Cleanup          : luksmeta-9-4.el8.x86_64                           937/1201 
  Cleanup          : libedit-3.1-23.20170329cvs.el8.x86_64             938/1201 
  Cleanup          : rsyslog-relp-8.1911.0-7.el8.x86_64                939/1201 
  Cleanup          : librelp-1.2.16-1.el8.x86_64                       940/1201 
  Running scriptlet: librelp-1.2.16-1.el8.x86_64                       940/1201 
  Cleanup          : zip-3.0-23.el8.x86_64                             941/1201 
  Running scriptlet: time-1.9-3.el8.x86_64                             942/1201 
  Cleanup          : time-1.9-3.el8.x86_64                             942/1201 
  Cleanup          : lsof-4.93.2-1.el8.x86_64                          943/1201 
  Cleanup          : unzip-6.0-44.el8.x86_64                           944/1201 
  Cleanup          : libluksmeta-9-4.el8.x86_64                        945/1201 
  Running scriptlet: libluksmeta-9-4.el8.x86_64                        945/1201 
  Cleanup          : python3-cairo-1.16.3-6.el8.x86_64                 946/1201 
  Cleanup          : cairo-1.15.12-3.el8.x86_64                        947/1201 
  Cleanup          : fontconfig-2.13.1-3.el8.x86_64                    948/1201 
  Cleanup          : freetype-2.9.1-4.el8_3.1.x86_64                   949/1201 
  Cleanup          : libpng-2:1.6.34-5.el8.x86_64                      950/1201 
  Cleanup          : pixman-0.38.4-1.el8.x86_64                        951/1201 
  Cleanup          : libassuan-2.5.1-3.el8.x86_64                      952/1201 
  Cleanup          : libksba-1.3.5-7.el8.x86_64                        953/1201 
  Cleanup          : libslirp-4.3.1-1.module_el8.4.0+575+63b40ad7.x    954/1201 
  Cleanup          : libgusb-0.3.0-1.el8.x86_64                        955/1201 
  Cleanup          : libusbx-1.0.23-4.el8.x86_64                       956/1201 
  Cleanup          : libnet-1.1.6-15.el8.x86_64                        957/1201 
  Running scriptlet: libnet-1.1.6-15.el8.x86_64                        957/1201 
  Cleanup          : libipa_hbac-2.4.0-9.el8.x86_64                    958/1201 
  Running scriptlet: libipa_hbac-2.4.0-9.el8.x86_64                    958/1201 
  Cleanup          : bzip2-1.0.6-26.el8.x86_64                         959/1201 
  Cleanup          : gpm-libs-1.20.7-17.el8.x86_64                     960/1201 
  Running scriptlet: gpm-libs-1.20.7-17.el8.x86_64                     960/1201 
  Cleanup          : python3-pyyaml-3.12-12.el8.x86_64                 961/1201 
  Cleanup          : rsyslog-gnutls-8.1911.0-7.el8.x86_64              962/1201 
  Running scriptlet: rsyslog-8.1911.0-7.el8.x86_64                     963/1201 
  Cleanup          : rsyslog-8.1911.0-7.el8.x86_64                     963/1201 
  Running scriptlet: rsyslog-8.1911.0-7.el8.x86_64                     963/1201 
  Cleanup          : logrotate-3.14.0-4.el8.x86_64                     964/1201 
  Cleanup          : libfastjson-0.99.8-2.el8.x86_64                   965/1201 
  Running scriptlet: libfastjson-0.99.8-2.el8.x86_64                   965/1201 
  Running scriptlet: hostname-3.20-6.el8.x86_64                        966/1201 
  Cleanup          : hostname-3.20-6.el8.x86_64                        966/1201 
  Cleanup          : libestr-0.1.10-1.el8.x86_64                       967/1201 
  Running scriptlet: libestr-0.1.10-1.el8.x86_64                       967/1201 
  Cleanup          : libXext-1.3.4-1.el8.x86_64                        968/1201 
  Cleanup          : fuse3-3.2.1-12.el8.x86_64                         969/1201 
  Cleanup          : libndp-1.7-5.el8.x86_64                           970/1201 
  Running scriptlet: libndp-1.7-5.el8.x86_64                           970/1201 
  Cleanup          : desktop-file-utils-0.23-8.el8.x86_64              971/1201 
  Cleanup          : oniguruma-6.8.2-2.el8.x86_64                      972/1201 
  Running scriptlet: oniguruma-6.8.2-2.el8.x86_64                      972/1201 
  Cleanup          : libnfnetlink-1.0.1-13.el8.x86_64                  973/1201 
  Running scriptlet: libnfnetlink-1.0.1-13.el8.x86_64                  973/1201 
  Cleanup          : dosfstools-4.1-6.el8.x86_64                       974/1201 
  Cleanup          : libudisks2-2.9.0-6.el8.x86_64                     975/1201 
  Cleanup          : libtalloc-2.3.1-2.el8.x86_64                      976/1201 
  Cleanup          : libdaemon-0.14-15.el8.x86_64                      977/1201 
  Cleanup          : json-glib-1.4.4-1.el8.x86_64                      978/1201 
  Cleanup          : pkgconf-1.4.2-1.el8.x86_64                        979/1201 
  Running scriptlet: ipset-7.1-1.el8.x86_64                            980/1201 
  Cleanup          : ipset-7.1-1.el8.x86_64                            980/1201 
  Cleanup          : ipset-libs-7.1-1.el8.x86_64                       981/1201 
  Running scriptlet: ipset-libs-7.1-1.el8.x86_64                       981/1201 
  Cleanup          : libmnl-1.0.4-6.el8.x86_64                         982/1201 
  Running scriptlet: libmnl-1.0.4-6.el8.x86_64                         982/1201 
  Cleanup          : vim-common-2:8.0.1763-15.el8.x86_64               983/1201 
  Cleanup          : virt-what-1.18-6.el8.x86_64                       984/1201 
  Cleanup          : hdparm-9.54-3.el8.x86_64                          985/1201 
  Cleanup          : libXrender-0.9.10-7.el8.x86_64                    986/1201 
  Cleanup          : libX11-1.6.8-4.el8.x86_64                         987/1201 
  Cleanup          : libxcb-1.13.1-1.el8.x86_64                        988/1201 
  Cleanup          : yajl-2.1.0-10.el8.x86_64                          989/1201 
  Cleanup          : libcollection-0.7.0-39.el8.x86_64                 990/1201 
  Cleanup          : libsss_autofs-2.4.0-9.el8.x86_64                  991/1201 
  Cleanup          : kernel-tools-libs-4.18.0-305.3.1.el8.x86_64       992/1201 
  Running scriptlet: kernel-tools-libs-4.18.0-305.3.1.el8.x86_64       992/1201 
  Cleanup          : lsscsi-0.32-2.el8.x86_64                          993/1201 
  Cleanup          : libsysfs-2.1.0-24.el8.x86_64                      994/1201 
  Running scriptlet: libsysfs-2.1.0-24.el8.x86_64                      994/1201 
  Cleanup          : dmidecode-1:3.2-8.el8.x86_64                      995/1201 
  Cleanup          : libpkgconf-1.4.2-1.el8.x86_64                     996/1201 
  Cleanup          : libyaml-0.1.7-5.el8.x86_64                        997/1201 
  Cleanup          : jansson-2.11-3.el8.x86_64                         998/1201 
  Cleanup          : libstemmer-0-10.585svn.el8.x86_64                 999/1201 
  Running scriptlet: libstemmer-0-10.585svn.el8.x86_64                 999/1201 
  Cleanup          : tree-1.7.0-15.el8.x86_64                         1000/1201 
  Cleanup          : python3-slip-dbus-0.6.4-11.el8.noarch            1001/1201 
  Cleanup          : python3-dbus-1.2.4-15.el8.x86_64                 1002/1201 
  Cleanup          : dbus-glib-0.110-2.el8.x86_64                     1003/1201 
  Running scriptlet: dbus-glib-0.110-2.el8.x86_64                     1003/1201 
  Cleanup          : libXau-1.0.9-3.el8.x86_64                        1004/1201 
  Cleanup          : lzo-2.08-14.el8.x86_64                           1005/1201 
  Cleanup          : protobuf-c-1.3.0-6.el8.x86_64                    1006/1201 
  Cleanup          : libbasicobjects-0.1.1-39.el8.x86_64              1007/1201 
  Cleanup          : libref_array-0.1.5-39.el8.x86_64                 1008/1201 
  Cleanup          : libdhash-0.5.0-39.el8.x86_64                     1009/1201 
  Cleanup          : symlinks-1.4-19.el8.x86_64                       1010/1201 
  Cleanup          : dos2unix-7.4.0-3.el8.x86_64                      1011/1201 
  Cleanup          : libaio-0.3.112-1.el8.x86_64                      1012/1201 
  Cleanup          : libpath_utils-0.2.1-39.el8.x86_64                1013/1201 
  Cleanup          : python3-slip-0.6.4-11.el8.noarch                 1014/1201 
  Cleanup          : policycoreutils-python-utils-2.9-14.el8.noarch   1015/1201 
  Cleanup          : python3-policycoreutils-2.9-14.el8.noarch        1016/1201 
  Cleanup          : python3-pydbus-0.6.0-5.el8.noarch                1017/1201 
  Cleanup          : python3-decorator-4.2.1-2.el8.noarch             1018/1201 
  Cleanup          : python3-six-1.11.0-8.el8.noarch                  1019/1201 
  Cleanup          : abattis-cantarell-fonts-0.0.25-6.el8.noarch      1020/1201 
  Cleanup          : fontpackages-filesystem-1.44-22.el8.noarch       1021/1201 
  Cleanup          : libX11-common-1.6.8-4.el8.noarch                 1022/1201 
  Cleanup          : vim-filesystem-2:8.0.1763-15.el8.noarch          1023/1201 
  Cleanup          : emacs-filesystem-1:26.1-5.el8.noarch             1024/1201 
  Cleanup          : fuse-common-3.2.1-12.el8.x86_64                  1025/1201 
  Cleanup          : geolite2-city-20180605-1.el8.noarch              1026/1201 
  Cleanup          : geolite2-country-20180605-1.el8.noarch           1027/1201 
  Running scriptlet: policycoreutils-2.9-14.el8.x86_64                1028/1201 
  Cleanup          : policycoreutils-2.9-14.el8.x86_64                1028/1201 
  Cleanup          : python3-setools-4.3.0-2.el8.x86_64               1029/1201 
  Cleanup          : python3-libsemanage-2.9-6.el8.x86_64             1030/1201 
  Cleanup          : python3-libselinux-2.9-5.el8.x86_64              1031/1201 
  Cleanup          : libselinux-utils-2.9-5.el8.x86_64                1032/1201 
  Cleanup          : python3-gobject-base-3.28.3-2.el8.x86_64         1033/1201 
  Cleanup          : gobject-introspection-1.56.1-1.el8.x86_64        1034/1201 
  Cleanup          : python3-audit-3.0-0.17.20191104git1c2f876.el8.   1035/1201 
  Cleanup          : iptables-libs-1.8.4-17.el8.x86_64                1036/1201 
  Cleanup          : libpcap-14:1.9.1-5.el8.x86_64                    1037/1201 
  Cleanup          : libibverbs-32.0-4.el8.x86_64                     1038/1201 
  Running scriptlet: libibverbs-32.0-4.el8.x86_64                     1038/1201 
  Cleanup          : rdma-core-32.0-4.el8.x86_64                      1039/1201 
  Cleanup          : pciutils-3.7.0-1.el8.x86_64                      1040/1201 
  Cleanup          : cracklib-dicts-2.9.6-15.el8.x86_64               1041/1201 
  Cleanup          : platform-python-pip-9.0.3-19.el8.noarch          1042/1201 
  Cleanup          : procps-ng-3.3.15-6.el8.x86_64                    1043/1201 
  Cleanup          : kbd-2.0.4-10.el8.x86_64                          1044/1201 
  Cleanup          : dbus-tools-1:1.12.8-12.el8_4.2.x86_64            1045/1201 
  Cleanup          : dbus-libs-1:1.12.8-12.el8_4.2.x86_64             1046/1201 
  Running scriptlet: dbus-libs-1:1.12.8-12.el8_4.2.x86_64             1046/1201 
  Running scriptlet: dbus-daemon-1:1.12.8-12.el8_4.2.x86_64           1047/1201 
  Cleanup          : dbus-daemon-1:1.12.8-12.el8_4.2.x86_64           1047/1201 
  Running scriptlet: dbus-daemon-1:1.12.8-12.el8_4.2.x86_64           1047/1201 
  Cleanup          : systemd-pam-239-45.el8.x86_64                    1048/1201 
  Cleanup          : libfdisk-2.32.1-27.el8.x86_64                    1049/1201 
  Running scriptlet: libfdisk-2.32.1-27.el8.x86_64                    1049/1201 
  Cleanup          : libmount-2.32.1-27.el8.x86_64                    1050/1201 
  Running scriptlet: libmount-2.32.1-27.el8.x86_64                    1050/1201 
  Cleanup          : libutempter-1.1.6-14.el8.x86_64                  1051/1201 
  Cleanup          : libpwquality-1.4.4-3.el8.x86_64                  1052/1201 
  Cleanup          : cracklib-2.9.6-15.el8.x86_64                     1053/1201 
  Cleanup          : ca-certificates-2020.2.41-80.0.el8_2.noarch      1054/1201 
  Cleanup          : platform-python-setuptools-39.2.0-6.el8.noarch   1055/1201 
  Cleanup          : shared-mime-info-1.9-3.el8.x86_64                1056/1201 
  Cleanup          : libblkid-2.32.1-27.el8.x86_64                    1057/1201 
  Running scriptlet: libblkid-2.32.1-27.el8.x86_64                    1057/1201 
  Cleanup          : systemd-libs-239-45.el8.x86_64                   1058/1201 
  Cleanup          : shadow-utils-2:4.6-12.el8.x86_64                 1059/1201 
  Cleanup          : libnsl2-1.2.0-2.20180605git4a062cf.el8.x86_64    1060/1201 
  Running scriptlet: libnsl2-1.2.0-2.20180605git4a062cf.el8.x86_64    1060/1201 
  Running scriptlet: gzip-1.9-12.el8.x86_64                           1061/1201 
  Cleanup          : gzip-1.9-12.el8.x86_64                           1061/1201 
  Cleanup          : pam-1.3.1-14.el8.x86_64                          1062/1201 
  Running scriptlet: pam-1.3.1-14.el8.x86_64                          1062/1201 
  Cleanup          : util-linux-2.32.1-27.el8.x86_64                  1063/1201 
  Cleanup          : openssl-pkcs11-0.4.10-2.el8.x86_64               1064/1201 
  Cleanup          : openssl-1:1.1.1g-15.el8_3.x86_64                 1065/1201 
  Cleanup          : libdb-utils-5.3.28-40.el8.x86_64                 1066/1201 
  Cleanup          : cyrus-sasl-lib-2.1.27-5.el8.x86_64               1067/1201 
  Running scriptlet: cyrus-sasl-lib-2.1.27-5.el8.x86_64               1067/1201 
  Cleanup          : openldap-2.4.46-16.el8.x86_64                    1068/1201 
  Cleanup          : libcurl-7.61.1-18.el8.x86_64                     1069/1201 
  Cleanup          : libssh-0.9.4-2.el8.x86_64                        1070/1201 
  Cleanup          : curl-7.61.1-18.el8.x86_64                        1071/1201 
  Cleanup          : libarchive-3.3.3-1.el8.x86_64                    1072/1201 
  Cleanup          : python3-libs-3.6.8-37.el8.x86_64                 1073/1201 
  Cleanup          : libtirpc-1.1.4-4.el8.x86_64                      1074/1201 
  Running scriptlet: libtirpc-1.1.4-4.el8.x86_64                      1074/1201 
  Cleanup          : krb5-libs-1.18.2-8.el8.x86_64                    1075/1201 
  Cleanup          : platform-python-3.6.8-37.el8.x86_64              1076/1201 
  Running scriptlet: platform-python-3.6.8-37.el8.x86_64              1076/1201 
  Cleanup          : kmod-25-17.el8.x86_64                            1077/1201 
  Cleanup          : trousers-lib-0.3.15-1.el8.x86_64                 1078/1201 
  Running scriptlet: trousers-lib-0.3.15-1.el8.x86_64                 1078/1201 
  Cleanup          : kmod-libs-25-17.el8.x86_64                       1079/1201 
  Running scriptlet: kmod-libs-25-17.el8.x86_64                       1079/1201 
  Cleanup          : coreutils-8.30-8.el8.x86_64                      1080/1201 
  Cleanup          : libdb-5.3.28-40.el8.x86_64                       1081/1201 
  Running scriptlet: libdb-5.3.28-40.el8.x86_64                       1081/1201 
  Cleanup          : rpm-4.14.3-13.el8.x86_64                         1082/1201 
  Cleanup          : rpm-libs-4.14.3-13.el8.x86_64                    1083/1201 
  Running scriptlet: rpm-libs-4.14.3-13.el8.x86_64                    1083/1201 
  Cleanup          : openssl-libs-1:1.1.1g-15.el8_3.x86_64            1084/1201 
  Running scriptlet: openssl-libs-1:1.1.1g-15.el8_3.x86_64            1084/1201 
  Cleanup          : crypto-policies-20210209-1.gitbfb6bed.el8_3.no   1085/1201 
  Cleanup          : crypto-policies-scripts-20210209-1.gitbfb6bed.   1086/1201 
  Cleanup          : grubby-8.40-41.el8.x86_64                        1087/1201 
  Running scriptlet: grub2-tools-1:2.02-99.el8.x86_64                 1088/1201 
  Cleanup          : grub2-tools-1:2.02-99.el8.x86_64                 1088/1201 
  Cleanup          : dracut-049-135.git20210121.el8.x86_64            1089/1201 
  Cleanup          : grub2-tools-minimal-1:2.02-99.el8.x86_64         1090/1201 
  Running scriptlet: gettext-0.19.8.1-17.el8.x86_64                   1091/1201 
  Cleanup          : gettext-0.19.8.1-17.el8.x86_64                   1091/1201 
  Cleanup          : gettext-libs-0.19.8.1-17.el8.x86_64              1092/1201 
  Cleanup          : libkcapi-hmaccalc-1.2.0-2.el8.x86_64             1093/1201 
  Cleanup          : os-prober-1.74-6.el8.x86_64                      1094/1201 
  Cleanup          : systemd-udev-239-45.el8.x86_64                   1095/1201 
  Running scriptlet: systemd-udev-239-45.el8.x86_64                   1095/1201 
  Cleanup          : libkcapi-1.2.0-2.el8.x86_64                      1096/1201 
  Cleanup          : kpartx-0.8.4-10.el8.x86_64                       1097/1201 
  Cleanup          : libcroco-0.6.12-4.el8_2.1.x86_64                 1098/1201 
  Running scriptlet: libcroco-0.6.12-4.el8_2.1.x86_64                 1098/1201 
  Cleanup          : glib2-2.56.4-10.el8_4.x86_64                     1099/1201 
  Cleanup          : cryptsetup-libs-2.3.3-4.el8.x86_64               1100/1201 
  Running scriptlet: cryptsetup-libs-2.3.3-4.el8.x86_64               1100/1201 
  Cleanup          : elfutils-libs-0.182-3.el8.x86_64                 1101/1201 
  Cleanup          : elfutils-default-yama-scope-0.182-3.el8.noarch   1102/1201 
  Cleanup          : gnutls-3.6.14-8.el8_3.x86_64                     1103/1201 
  Running scriptlet: trousers-0.3.15-1.el8.x86_64                     1104/1201 
  Cleanup          : trousers-0.3.15-1.el8.x86_64                     1104/1201 
  Running scriptlet: trousers-0.3.15-1.el8.x86_64                     1104/1201 
  Cleanup          : device-mapper-libs-8:1.02.175-5.el8.x86_64       1105/1201 
  Cleanup          : device-mapper-8:1.02.175-5.el8.x86_64            1106/1201 
  Cleanup          : dbus-1:1.12.8-12.el8_4.2.x86_64                  1107/1201 
  Running scriptlet: systemd-239-45.el8.x86_64                        1108/1201 
  Cleanup          : systemd-239-45.el8.x86_64                        1108/1201 
  Cleanup          : p11-kit-trust-0.23.22-1.el8.x86_64               1109/1201 
  Running scriptlet: p11-kit-trust-0.23.22-1.el8.x86_64               1109/1201 
  Cleanup          : p11-kit-0.23.22-1.el8.x86_64                     1110/1201 
  Cleanup          : libstdc++-8.4.1-1.el8.x86_64                     1111/1201 
  Running scriptlet: libstdc++-8.4.1-1.el8.x86_64                     1111/1201 
  Cleanup          : libxml2-2.9.7-9.el8.x86_64                       1112/1201 
  Running scriptlet: libgomp-8.4.1-1.el8.x86_64                       1113/1201 
  Cleanup          : libgomp-8.4.1-1.el8.x86_64                       1113/1201 
  Running scriptlet: libgomp-8.4.1-1.el8.x86_64                       1113/1201 
  Cleanup          : pigz-2.4-4.el8.x86_64                            1114/1201 
  Cleanup          : xz-5.2.4-3.el8.x86_64                            1115/1201 
  Cleanup          : gawk-4.2.1-2.el8.x86_64                          1116/1201 
  Cleanup          : libsemanage-2.9-6.el8.x86_64                     1117/1201 
  Running scriptlet: findutils-1:4.6.0-20.el8.x86_64                  1118/1201 
  Cleanup          : findutils-1:4.6.0-20.el8.x86_64                  1118/1201 
  Cleanup          : libsmartcols-2.32.1-27.el8.x86_64                1119/1201 
  Running scriptlet: libsmartcols-2.32.1-27.el8.x86_64                1119/1201 
  Cleanup          : libnl3-3.5.0-1.el8.x86_64                        1120/1201 
  Running scriptlet: libnl3-3.5.0-1.el8.x86_64                        1120/1201 
  Cleanup          : mpfr-3.1.6-1.el8.x86_64                          1121/1201 
  Running scriptlet: mpfr-3.1.6-1.el8.x86_64                          1121/1201 
  Running scriptlet: sed-4.5-2.el8.x86_64                             1122/1201 
  Cleanup          : sed-4.5-2.el8.x86_64                             1122/1201 
  Running scriptlet: grep-3.1-6.el8.x86_64                            1123/1201 
  Cleanup          : grep-3.1-6.el8.x86_64                            1123/1201 
  Cleanup          : sqlite-libs-3.26.0-13.el8.x86_64                 1124/1201 
  Cleanup          : chkconfig-1.13-2.el8.x86_64                      1125/1201 
  Cleanup          : libgcrypt-1.8.5-4.el8.x86_64                     1126/1201 
  Running scriptlet: libgcrypt-1.8.5-4.el8.x86_64                     1126/1201 
  Running scriptlet: diffutils-3.6-6.el8.x86_64                       1127/1201 
  Cleanup          : diffutils-3.6-6.el8.x86_64                       1127/1201 
  Running scriptlet: nettle-3.4.1-4.el8_3.x86_64                      1128/1201 
  Cleanup          : nettle-3.4.1-4.el8_3.x86_64                      1128/1201 
  Running scriptlet: nettle-3.4.1-4.el8_3.x86_64                      1128/1201 
  Cleanup          : libuuid-2.32.1-27.el8.x86_64                     1129/1201 
  Running scriptlet: libuuid-2.32.1-27.el8.x86_64                     1129/1201 
  Cleanup          : xz-libs-5.2.4-3.el8.x86_64                       1130/1201 
  Cleanup          : lua-libs-5.3.4-11.el8.x86_64                     1131/1201 
  Cleanup          : libcom_err-1.45.6-1.el8.x86_64                   1132/1201 
  Running scriptlet: libcom_err-1.45.6-1.el8.x86_64                   1132/1201 
  Cleanup          : gdbm-1:1.18-1.el8.x86_64                         1133/1201 
  Running scriptlet: readline-7.0-10.el8.x86_64                       1134/1201 
  Cleanup          : readline-7.0-10.el8.x86_64                       1134/1201 
  Running scriptlet: readline-7.0-10.el8.x86_64                       1134/1201 
  Cleanup          : pciutils-libs-3.7.0-1.el8.x86_64                 1135/1201 
  Running scriptlet: pciutils-libs-3.7.0-1.el8.x86_64                 1135/1201 
  Cleanup          : audit-libs-3.0-0.17.20191104git1c2f876.el8.x86   1136/1201 
  Cleanup          : memstrack-0.1.11-1.el8.x86_64                    1137/1201 
  Cleanup          : libcap-ng-0.7.9-5.el8.x86_64                     1138/1201 
  Cleanup          : gmp-1:6.1.2-10.el8.x86_64                        1139/1201 
  Running scriptlet: gmp-1:6.1.2-10.el8.x86_64                        1139/1201 
  Cleanup          : popt-1.18-1.el8.x86_64                           1140/1201 
  Cleanup          : acl-2.2.53-1.el8.x86_64                          1141/1201 
  Cleanup          : json-c-0.13.1-0.4.el8.x86_64                     1142/1201 
  Cleanup          : ncurses-6.1-7.20180224.el8.x86_64                1143/1201 
  Cleanup          : gdbm-libs-1:1.18-1.el8.x86_64                    1144/1201 
  Cleanup          : libgpg-error-1.31-1.el8.x86_64                   1145/1201 
  Cleanup          : pcre-8.42-4.el8.x86_64                           1146/1201 
  Cleanup          : libtasn1-4.13-3.el8.x86_64                       1147/1201 
  Running scriptlet: libtasn1-4.13-3.el8.x86_64                       1147/1201 
  Cleanup          : libcap-2.26-4.el8.x86_64                         1148/1201 
  Cleanup          : elfutils-libelf-0.182-3.el8.x86_64               1149/1201 
  Cleanup          : libxkbcommon-0.9.1-1.el8.x86_64                  1150/1201 
  Cleanup          : cpio-2.12-10.el8.x86_64                          1151/1201 
  Cleanup          : libverto-0.3.0-5.el8.x86_64                      1152/1201 
  Cleanup          : libpsl-0.20.2-6.el8.x86_64                       1153/1201 
  Cleanup          : libacl-2.2.53-1.el8.x86_64                       1154/1201 
  Cleanup          : libxcrypt-4.1.1-4.el8.x86_64                     1155/1201 
  Cleanup          : file-5.33-16.el8_3.1.x86_64                      1156/1201 
  Cleanup          : file-libs-5.33-16.el8_3.1.x86_64                 1157/1201 
  Cleanup          : keyutils-libs-1.5.10-6.el8.x86_64                1158/1201 
  Cleanup          : brotli-1.0.6-3.el8.x86_64                        1159/1201 
  Cleanup          : libidn2-2.2.0-1.el8.x86_64                       1160/1201 
  Cleanup          : libunistring-0.9.9-3.el8.x86_64                  1161/1201 
  Cleanup          : libseccomp-2.5.1-1.el8.x86_64                    1162/1201 
  Running scriptlet: libseccomp-2.5.1-1.el8.x86_64                    1162/1201 
  Cleanup          : hardlink-1:1.3-6.el8.x86_64                      1163/1201 
  Cleanup          : which-2.21-12.el8.x86_64                         1164/1201 
  Cleanup          : checkpolicy-2.9-1.el8.x86_64                     1165/1201 
  Running scriptlet: coreutils-common-8.30-8.el8.x86_64               1166/1201 
  Cleanup          : coreutils-common-8.30-8.el8.x86_64               1166/1201 
  Cleanup          : grub2-common-1:2.02-99.el8.noarch                1167/1201 
  Cleanup          : publicsuffix-list-dafsa-20180723-1.el8.noarch    1168/1201 
  Cleanup          : xkeyboard-config-2.28-1.el8.noarch               1169/1201 
  Cleanup          : python3-pip-wheel-9.0.3-19.el8.noarch            1170/1201 
  Cleanup          : python3-setuptools-wheel-39.2.0-6.el8.noarch     1171/1201 
  Cleanup          : libssh-config-0.9.4-2.el8.noarch                 1172/1201 
  Cleanup          : dbus-common-1:1.12.8-12.el8_4.2.noarch           1173/1201 
  Cleanup          : kbd-legacy-2.0.4-10.el8.noarch                   1174/1201 
  Cleanup          : kbd-misc-2.0.4-10.el8.noarch                     1175/1201 
  Cleanup          : hwdata-0.314-8.8.el8.noarch                      1176/1201 
  Cleanup          : info-6.5-6.el8.x86_64                            1177/1201 
  Cleanup          : zlib-1.2.11-17.el8.x86_64                        1178/1201 
  Cleanup          : bzip2-libs-1.0.6-26.el8.x86_64                   1179/1201 
  Cleanup          : libffi-3.1-22.el8.x86_64                         1180/1201 
  Cleanup          : libzstd-1.4.4-1.el8.x86_64                       1181/1201 
  Cleanup          : libmetalink-0.1.3-7.el8.x86_64                   1182/1201 
  Cleanup          : expat-2.2.5-4.el8.x86_64                         1183/1201 
  Cleanup          : libnghttp2-1.33.0-3.el8_2.1.x86_64               1184/1201 
  Cleanup          : libattr-2.4.48-3.el8.x86_64                      1185/1201 
  Cleanup          : lz4-libs-1.8.3-2.el8.x86_64                      1186/1201 
  Cleanup          : libsigsegv-2.11-5.el8.x86_64                     1187/1201 
  Cleanup          : glibc-langpack-en-2.28-151.el8.x86_64            1188/1201 
  Cleanup          : glibc-common-2.28-151.el8.x86_64                 1189/1201 
  Cleanup          : libselinux-2.9-5.el8.x86_64                      1190/1201 
  Cleanup          : libsepol-2.9-2.el8.x86_64                        1191/1201 
  Running scriptlet: libsepol-2.9-2.el8.x86_64                        1191/1201 
  Cleanup          : bash-4.4.20-1.el8_4.x86_64                       1192/1201 
  Running scriptlet: bash-4.4.20-1.el8_4.x86_64                       1192/1201 
  Cleanup          : ncurses-libs-6.1-7.20180224.el8.x86_64           1193/1201 
  Cleanup          : pcre2-10.32-2.el8.x86_64                         1194/1201 
  Cleanup          : glibc-2.28-151.el8.x86_64                        1195/1201 
  Cleanup          : basesystem-11-5.el8.noarch                       1196/1201 
  Cleanup          : filesystem-3.8-3.el8.x86_64                      1197/1201 
  Cleanup          : setup-2.12.2-6.el8.noarch                        1198/1201 
  Cleanup          : ncurses-base-6.1-7.20180224.el8.noarch           1199/1201 
  Cleanup          : tzdata-2021a-1.el8.noarch                        1200/1201 
  Cleanup          : libgcc-8.4.1-1.el8.x86_64                        1201/1201 
  Running scriptlet: libgcc-8.4.1-1.el8.x86_64                        1201/1201 
  Running scriptlet: filesystem-3.8-3.el8.x86_64                      1201/1201 
  Running scriptlet: crypto-policies-scripts-20210209-1.gitbfb6bed.   1201/1201 
  Running scriptlet: ca-certificates-2020.2.41-80.0.el8_2.noarch      1201/1201 
  Running scriptlet: kernel-core-4.18.0-305.3.1.el8_4.x86_64          1201/1201 
  Running scriptlet: libwbclient-4.13.3-3.el8.x86_64                  1201/1201 
  Running scriptlet: clevis-15-1.el8.x86_64                           1201/1201 
  Running scriptlet: kmod-kvdo-6.2.4.26-77.el8.x86_64                 1201/1201 
  Running scriptlet: container-selinux-2:2.162.0-1.module+el8.4.0+5   1201/1201 
  Running scriptlet: authselect-libs-1.2.2-2.el8.x86_64               1201/1201 
  Running scriptlet: nss-3.53.1-17.el8_3.x86_64                       1201/1201 
  Running scriptlet: sssd-common-2.4.0-9.el8.x86_64                   1201/1201 
  Running scriptlet: authselect-compat-1.2.2-2.el8.x86_64             1201/1201 
  Running scriptlet: tuned-2.15.0-2.el8.noarch                        1201/1201 
  Running scriptlet: microcode_ctl-4:20210216-1.20210525.1.el8_4.x8   1201/1201 
  Running scriptlet: rootfiles-8.1-22.el8.noarch                      1201/1201 
  Running scriptlet: libgcc-8.4.1-1.el8.x86_64                        1201/1201 
  Running scriptlet: glibc-common-2.28-151.el8.x86_64                 1201/1201 
  Running scriptlet: info-6.5-6.el8.x86_64                            1201/1201 
  Running scriptlet: glib2-2.56.4-10.el8_4.x86_64                     1201/1201 
  Running scriptlet: shared-mime-info-1.9-3.el8.x86_64                1201/1201 
  Running scriptlet: systemd-239-45.el8.x86_64                        1201/1201 
  Running scriptlet: systemd-udev-239-45.el8.x86_64                   1201/1201 
  Running scriptlet: fontconfig-2.13.1-3.el8.x86_64                   1201/1201 
  Running scriptlet: desktop-file-utils-0.23-8.el8.x86_64             1201/1201 
  Running scriptlet: vim-common-2:8.0.1763-15.el8.x86_64              1201/1201 
  Running scriptlet: man-db-2.7.6.1-17.el8.x86_64                     1201/1201 
  Verifying        : buildah-1.19.7-2.module+el8.4.0+556+40122d08.x      1/1201 
  Verifying        : buildah-1.19.7-2.module_el8.4.0+830+8027e1c4.x      2/1201 
  Verifying        : cockpit-podman-29-2.module+el8.4.0+556+40122d0      3/1201 
  Verifying        : cockpit-podman-29-2.module_el8.4.0+781+acf4c33      4/1201 
  Verifying        : conmon-2:2.0.26-3.module+el8.4.0+556+40122d08.      5/1201 
  Verifying        : conmon-2:2.0.26-3.module_el8.4.0+830+8027e1c4.      6/1201 
  Verifying        : container-selinux-2:2.162.0-1.module+el8.4.0+5      7/1201 
  Verifying        : container-selinux-2:2.162.0-1.module_el8.4.0+8      8/1201 
  Verifying        : containernetworking-plugins-0.9.1-1.module+el8      9/1201 
  Verifying        : containernetworking-plugins-0.9.1-1.module_el8     10/1201 
  Verifying        : containers-common-1:1.2.2-10.module+el8.4.0+55     11/1201 
  Verifying        : containers-common-1:1.2.2-10.module_el8.4.0+83     12/1201 
  Verifying        : criu-3.15-1.module+el8.4.0+556+40122d08.x86_64     13/1201 
  Verifying        : criu-3.15-1.module_el8.4.0+641+6116a774.x86_64     14/1201 
  Verifying        : crun-0.18-2.module+el8.4.0+556+40122d08.x86_64     15/1201 
  Verifying        : crun-0.18-2.module_el8.4.0+830+8027e1c4.x86_64     16/1201 
  Verifying        : fuse-overlayfs-1.4.0-3.module+el8.4.0+556+4012     17/1201 
  Verifying        : fuse-overlayfs-1.4.0-3.module_el8.4.0+830+8027     18/1201 
  Verifying        : libslirp-4.3.1-1.module+el8.4.0+556+40122d08.x     19/1201 
  Verifying        : libslirp-4.3.1-1.module_el8.4.0+575+63b40ad7.x     20/1201 
  Verifying        : podman-3.0.1-7.module+el8.4.0+556+40122d08.x86     21/1201 
  Verifying        : podman-3.0.1-7.module_el8.4.0+830+8027e1c4.x86     22/1201 
  Verifying        : podman-catatonit-3.0.1-7.module+el8.4.0+556+40     23/1201 
  Verifying        : podman-catatonit-3.0.1-7.module_el8.4.0+830+80     24/1201 
  Verifying        : runc-1.0.0-73.rc93.module+el8.4.0+556+40122d08     25/1201 
  Verifying        : runc-1.0.0-73.rc93.module_el8.4.0+830+8027e1c4     26/1201 
  Verifying        : slirp4netns-1.1.8-1.module+el8.4.0+556+40122d0     27/1201 
  Verifying        : slirp4netns-1.1.8-1.module_el8.4.0+641+6116a77     28/1201 
  Verifying        : dhcp-client-12:4.3.6-44.el8_4.1.x86_64             29/1201 
  Verifying        : dhcp-client-12:4.3.6-44.0.1.el8.x86_64             30/1201 
  Verifying        : dhcp-common-12:4.3.6-44.el8_4.1.noarch             31/1201 
  Verifying        : dhcp-common-12:4.3.6-44.0.1.el8.noarch             32/1201 
  Verifying        : dhcp-libs-12:4.3.6-44.el8_4.1.x86_64               33/1201 
  Verifying        : dhcp-libs-12:4.3.6-44.0.1.el8.x86_64               34/1201 
  Verifying        : nvme-cli-1.12-3.el8.x86_64                         35/1201 
  Verifying        : nvme-cli-1.12-3.el8.0.1.x86_64                     36/1201 
  Verifying        : PackageKit-1.1.12-6.el8.x86_64                     37/1201 
  Verifying        : PackageKit-1.1.12-6.el8.x86_64                     38/1201 
  Verifying        : PackageKit-glib-1.1.12-6.el8.x86_64                39/1201 
  Verifying        : PackageKit-glib-1.1.12-6.el8.x86_64                40/1201 
  Verifying        : abattis-cantarell-fonts-0.0.25-6.el8.noarch        41/1201 
  Verifying        : abattis-cantarell-fonts-0.0.25-6.el8.noarch        42/1201 
  Verifying        : authselect-compat-1.2.2-2.el8.x86_64               43/1201 
  Verifying        : authselect-compat-1.2.2-2.el8.x86_64               44/1201 
  Verifying        : bind-libs-32:9.11.26-4.el8_4.x86_64                45/1201 
  Verifying        : bind-libs-32:9.11.26-4.el8_4.x86_64                46/1201 
  Verifying        : bind-libs-lite-32:9.11.26-4.el8_4.x86_64           47/1201 
  Verifying        : bind-libs-lite-32:9.11.26-4.el8_4.x86_64           48/1201 
  Verifying        : bind-license-32:9.11.26-4.el8_4.noarch             49/1201 
  Verifying        : bind-license-32:9.11.26-4.el8_4.noarch             50/1201 
  Verifying        : bind-utils-32:9.11.26-4.el8_4.x86_64               51/1201 
  Verifying        : bind-utils-32:9.11.26-4.el8_4.x86_64               52/1201 
  Verifying        : cairo-1.15.12-3.el8.x86_64                         53/1201 
  Verifying        : cairo-1.15.12-3.el8.x86_64                         54/1201 
  Verifying        : cairo-gobject-1.15.12-3.el8.x86_64                 55/1201 
  Verifying        : cairo-gobject-1.15.12-3.el8.x86_64                 56/1201 
  Verifying        : clevis-15-1.el8.x86_64                             57/1201 
  Verifying        : clevis-15-1.el8.x86_64                             58/1201 
  Verifying        : clevis-luks-15-1.el8.x86_64                        59/1201 
  Verifying        : clevis-luks-15-1.el8.x86_64                        60/1201 
  Verifying        : cockpit-packagekit-238.2-1.el8.noarch              61/1201 
  Verifying        : cockpit-packagekit-238.2-1.el8.noarch              62/1201 
  Verifying        : cockpit-storaged-238.2-1.el8.noarch                63/1201 
  Verifying        : cockpit-storaged-238.2-1.el8.noarch                64/1201 
  Verifying        : desktop-file-utils-0.23-8.el8.x86_64               65/1201 
  Verifying        : desktop-file-utils-0.23-8.el8.x86_64               66/1201 
  Verifying        : fprintd-1.90.9-2.el8.x86_64                        67/1201 
  Verifying        : fprintd-1.90.9-2.el8.x86_64                        68/1201 
  Verifying        : fprintd-pam-1.90.9-2.el8.x86_64                    69/1201 
  Verifying        : fprintd-pam-1.90.9-2.el8.x86_64                    70/1201 
  Verifying        : fstrm-0.6.0-3.el8.1.x86_64                         71/1201 
  Verifying        : fstrm-0.6.0-3.el8.1.x86_64                         72/1201 
  Verifying        : geolite2-city-20180605-1.el8.noarch                73/1201 
  Verifying        : geolite2-city-20180605-1.el8.noarch                74/1201 
  Verifying        : geolite2-country-20180605-1.el8.noarch             75/1201 
  Verifying        : geolite2-country-20180605-1.el8.noarch             76/1201 
  Verifying        : gpm-libs-1.20.7-17.el8.x86_64                      77/1201 
  Verifying        : gpm-libs-1.20.7-17.el8.x86_64                      78/1201 
  Verifying        : jose-10-2.el8.x86_64                               79/1201 
  Verifying        : jose-10-2.el8.x86_64                               80/1201 
  Verifying        : jq-1.5-12.el8.x86_64                               81/1201 
  Verifying        : jq-1.5-12.el8.x86_64                               82/1201 
  Verifying        : langpacks-en-1.0-12.el8.noarch                     83/1201 
  Verifying        : langpacks-en-1.0-12.el8.noarch                     84/1201 
  Verifying        : libX11-1.6.8-4.el8.x86_64                          85/1201 
  Verifying        : libX11-1.6.8-4.el8.x86_64                          86/1201 
  Verifying        : libX11-common-1.6.8-4.el8.noarch                   87/1201 
  Verifying        : libX11-common-1.6.8-4.el8.noarch                   88/1201 
  Verifying        : libXau-1.0.9-3.el8.x86_64                          89/1201 
  Verifying        : libXau-1.0.9-3.el8.x86_64                          90/1201 
  Verifying        : libXext-1.3.4-1.el8.x86_64                         91/1201 
  Verifying        : libXext-1.3.4-1.el8.x86_64                         92/1201 
  Verifying        : libXrender-0.9.10-7.el8.x86_64                     93/1201 
  Verifying        : libXrender-0.9.10-7.el8.x86_64                     94/1201 
  Verifying        : libatasmart-0.19-14.el8.x86_64                     95/1201 
  Verifying        : libatasmart-0.19-14.el8.x86_64                     96/1201 
  Verifying        : libblockdev-2.24-5.el8.x86_64                      97/1201 
  Verifying        : libblockdev-2.24-5.el8.x86_64                      98/1201 
  Verifying        : libblockdev-crypto-2.24-5.el8.x86_64               99/1201 
  Verifying        : libblockdev-crypto-2.24-5.el8.x86_64              100/1201 
  Verifying        : libblockdev-fs-2.24-5.el8.x86_64                  101/1201 
  Verifying        : libblockdev-fs-2.24-5.el8.x86_64                  102/1201 
  Verifying        : libblockdev-loop-2.24-5.el8.x86_64                103/1201 
  Verifying        : libblockdev-loop-2.24-5.el8.x86_64                104/1201 
  Verifying        : libblockdev-lvm-2.24-5.el8.x86_64                 105/1201 
  Verifying        : libblockdev-lvm-2.24-5.el8.x86_64                 106/1201 
  Verifying        : libblockdev-mdraid-2.24-5.el8.x86_64              107/1201 
  Verifying        : libblockdev-mdraid-2.24-5.el8.x86_64              108/1201 
  Verifying        : libblockdev-part-2.24-5.el8.x86_64                109/1201 
  Verifying        : libblockdev-part-2.24-5.el8.x86_64                110/1201 
  Verifying        : libblockdev-swap-2.24-5.el8.x86_64                111/1201 
  Verifying        : libblockdev-swap-2.24-5.el8.x86_64                112/1201 
  Verifying        : libblockdev-utils-2.24-5.el8.x86_64               113/1201 
  Verifying        : libblockdev-utils-2.24-5.el8.x86_64               114/1201 
  Verifying        : libbytesize-1.4-3.el8.x86_64                      115/1201 
  Verifying        : libbytesize-1.4-3.el8.x86_64                      116/1201 
  Verifying        : libestr-0.1.10-1.el8.x86_64                       117/1201 
  Verifying        : libestr-0.1.10-1.el8.x86_64                       118/1201 
  Verifying        : libfastjson-0.99.8-2.el8.x86_64                   119/1201 
  Verifying        : libfastjson-0.99.8-2.el8.x86_64                   120/1201 
  Verifying        : libfprint-1.90.7-1.el8.x86_64                     121/1201 
  Verifying        : libfprint-1.90.7-1.el8.x86_64                     122/1201 
  Verifying        : libjose-10-2.el8.x86_64                           123/1201 
  Verifying        : libjose-10-2.el8.x86_64                           124/1201 
  Verifying        : libluksmeta-9-4.el8.x86_64                        125/1201 
  Verifying        : libluksmeta-9-4.el8.x86_64                        126/1201 
  Verifying        : libmaxminddb-1.2.0-10.el8.x86_64                  127/1201 
  Verifying        : libmaxminddb-1.2.0-10.el8.x86_64                  128/1201 
  Verifying        : libnet-1.1.6-15.el8.x86_64                        129/1201 
  Verifying        : libnet-1.1.6-15.el8.x86_64                        130/1201 
  Verifying        : librelp-1.2.16-1.el8.x86_64                       131/1201 
  Verifying        : librelp-1.2.16-1.el8.x86_64                       132/1201 
  Verifying        : libudisks2-2.9.0-6.el8.x86_64                     133/1201 
  Verifying        : libudisks2-2.9.0-6.el8.x86_64                     134/1201 
  Verifying        : libxcb-1.13.1-1.el8.x86_64                        135/1201 
  Verifying        : libxcb-1.13.1-1.el8.x86_64                        136/1201 
  Verifying        : libxkbcommon-0.9.1-1.el8.x86_64                   137/1201 
  Verifying        : libxkbcommon-0.9.1-1.el8.x86_64                   138/1201 
  Verifying        : luksmeta-9-4.el8.x86_64                           139/1201 
  Verifying        : luksmeta-9-4.el8.x86_64                           140/1201 
  Verifying        : man-pages-overrides-8.3.0.2-2.el8.noarch          141/1201 
  Verifying        : man-pages-overrides-8.3.0.2-2.el8.noarch          142/1201 
  Verifying        : nmap-ncat-2:7.70-5.el8.x86_64                     143/1201 
  Verifying        : nmap-ncat-2:7.70-5.el8.x86_64                     144/1201 
  Verifying        : nspr-4.25.0-2.el8_2.x86_64                        145/1201 
  Verifying        : nspr-4.25.0-2.el8_2.x86_64                        146/1201 
  Verifying        : nss-3.53.1-17.el8_3.x86_64                        147/1201 
  Verifying        : nss-3.53.1-17.el8_3.x86_64                        148/1201 
  Verifying        : nss-softokn-3.53.1-17.el8_3.x86_64                149/1201 
  Verifying        : nss-softokn-3.53.1-17.el8_3.x86_64                150/1201 
  Verifying        : nss-softokn-freebl-3.53.1-17.el8_3.x86_64         151/1201 
  Verifying        : nss-softokn-freebl-3.53.1-17.el8_3.x86_64         152/1201 
  Verifying        : nss-sysinit-3.53.1-17.el8_3.x86_64                153/1201 
  Verifying        : nss-sysinit-3.53.1-17.el8_3.x86_64                154/1201 
  Verifying        : nss-util-3.53.1-17.el8_3.x86_64                   155/1201 
  Verifying        : nss-util-3.53.1-17.el8_3.x86_64                   156/1201 
  Verifying        : oddjob-0.34.7-1.el8.x86_64                        157/1201 
  Verifying        : oddjob-0.34.7-1.el8.x86_64                        158/1201 
  Verifying        : oddjob-mkhomedir-0.34.7-1.el8.x86_64              159/1201 
  Verifying        : oddjob-mkhomedir-0.34.7-1.el8.x86_64              160/1201 
  Verifying        : oniguruma-6.8.2-2.el8.x86_64                      161/1201 
  Verifying        : oniguruma-6.8.2-2.el8.x86_64                      162/1201 
  Verifying        : pinentry-1.1.0-2.el8.x86_64                       163/1201 
  Verifying        : pinentry-1.1.0-2.el8.x86_64                       164/1201 
  Verifying        : pinfo-0.6.10-18.el8.x86_64                        165/1201 
  Verifying        : pinfo-0.6.10-18.el8.x86_64                        166/1201 
  Verifying        : pixman-0.38.4-1.el8.x86_64                        167/1201 
  Verifying        : pixman-0.38.4-1.el8.x86_64                        168/1201 
  Verifying        : plymouth-0.9.4-9.20200615git1e36e30.el8.x86_64    169/1201 
  Verifying        : plymouth-0.9.4-9.20200615git1e36e30.el8.x86_64    170/1201 
  Verifying        : plymouth-core-libs-0.9.4-9.20200615git1e36e30.    171/1201 
  Verifying        : plymouth-core-libs-0.9.4-9.20200615git1e36e30.    172/1201 
  Verifying        : plymouth-scripts-0.9.4-9.20200615git1e36e30.el    173/1201 
  Verifying        : plymouth-scripts-0.9.4-9.20200615git1e36e30.el    174/1201 
  Verifying        : protobuf-c-1.3.0-6.el8.x86_64                     175/1201 
  Verifying        : protobuf-c-1.3.0-6.el8.x86_64                     176/1201 
  Verifying        : python3-bind-32:9.11.26-4.el8_4.noarch            177/1201 
  Verifying        : python3-bind-32:9.11.26-4.el8_4.noarch            178/1201 
  Verifying        : python3-cairo-1.16.3-6.el8.x86_64                 179/1201 
  Verifying        : python3-cairo-1.16.3-6.el8.x86_64                 180/1201 
  Verifying        : python3-gobject-3.28.3-2.el8.x86_64               181/1201 
  Verifying        : python3-gobject-3.28.3-2.el8.x86_64               182/1201 
  Verifying        : python3-html5lib-1:0.999999999-6.el8.noarch       183/1201 
  Verifying        : python3-html5lib-1:0.999999999-6.el8.noarch       184/1201 
  Verifying        : python3-lxml-4.2.3-2.el8.x86_64                   185/1201 
  Verifying        : python3-lxml-4.2.3-2.el8.x86_64                   186/1201 
  Verifying        : python3-pexpect-4.3.1-3.el8.noarch                187/1201 
  Verifying        : python3-pexpect-4.3.1-3.el8.noarch                188/1201 
  Verifying        : python3-psutil-5.4.3-10.el8.x86_64                189/1201 
  Verifying        : python3-psutil-5.4.3-10.el8.x86_64                190/1201 
  Verifying        : python3-ptyprocess-0.5.2-4.el8.noarch             191/1201 
  Verifying        : python3-ptyprocess-0.5.2-4.el8.noarch             192/1201 
  Verifying        : python3-pydbus-0.6.0-5.el8.noarch                 193/1201 
  Verifying        : python3-pydbus-0.6.0-5.el8.noarch                 194/1201 
  Verifying        : python3-systemd-234-8.el8.x86_64                  195/1201 
  Verifying        : python3-systemd-234-8.el8.x86_64                  196/1201 
  Verifying        : python3-tracer-0.7.5-2.el8.noarch                 197/1201 
  Verifying        : python3-tracer-0.7.5-2.el8.noarch                 198/1201 
  Verifying        : python3-unbound-1.7.3-15.el8.x86_64               199/1201 
  Verifying        : python3-unbound-1.7.3-15.el8.x86_64               200/1201 
  Verifying        : python3-webencodings-0.5.1-6.el8.noarch           201/1201 
  Verifying        : python3-webencodings-0.5.1-6.el8.noarch           202/1201 
  Verifying        : setroubleshoot-plugins-3.3.13-1.el8.noarch        203/1201 
  Verifying        : setroubleshoot-plugins-3.3.13-1.el8.noarch        204/1201 
  Verifying        : setroubleshoot-server-3.3.24-3.el8.x86_64         205/1201 
  Verifying        : setroubleshoot-server-3.3.24-3.el8.x86_64         206/1201 
  Verifying        : sscg-2.3.3-14.el8.x86_64                          207/1201 
  Verifying        : sscg-2.3.3-14.el8.x86_64                          208/1201 
  Verifying        : tcpdump-14:4.9.3-1.el8.x86_64                     209/1201 
  Verifying        : tcpdump-14:4.9.3-1.el8.x86_64                     210/1201 
  Verifying        : tracer-common-0.7.5-2.el8.noarch                  211/1201 
  Verifying        : tracer-common-0.7.5-2.el8.noarch                  212/1201 
  Verifying        : udisks2-2.9.0-6.el8.x86_64                        213/1201 
  Verifying        : udisks2-2.9.0-6.el8.x86_64                        214/1201 
  Verifying        : udisks2-iscsi-2.9.0-6.el8.x86_64                  215/1201 
  Verifying        : udisks2-iscsi-2.9.0-6.el8.x86_64                  216/1201 
  Verifying        : udisks2-lvm2-2.9.0-6.el8.x86_64                   217/1201 
  Verifying        : udisks2-lvm2-2.9.0-6.el8.x86_64                   218/1201 
  Verifying        : unbound-libs-1.7.3-15.el8.x86_64                  219/1201 
  Verifying        : unbound-libs-1.7.3-15.el8.x86_64                  220/1201 
  Verifying        : vim-common-2:8.0.1763-15.el8.x86_64               221/1201 
  Verifying        : vim-common-2:8.0.1763-15.el8.x86_64               222/1201 
  Verifying        : vim-enhanced-2:8.0.1763-15.el8.x86_64             223/1201 
  Verifying        : vim-enhanced-2:8.0.1763-15.el8.x86_64             224/1201 
  Verifying        : vim-filesystem-2:8.0.1763-15.el8.noarch           225/1201 
  Verifying        : vim-filesystem-2:8.0.1763-15.el8.noarch           226/1201 
  Verifying        : volume_key-libs-0.3.11-5.el8.x86_64               227/1201 
  Verifying        : volume_key-libs-0.3.11-5.el8.x86_64               228/1201 
  Verifying        : wget-1.19.5-10.el8.x86_64                         229/1201 
  Verifying        : wget-1.19.5-10.el8.x86_64                         230/1201 
  Verifying        : xdg-utils-1.1.2-5.el8.noarch                      231/1201 
  Verifying        : xdg-utils-1.1.2-5.el8.noarch                      232/1201 
  Verifying        : xkeyboard-config-2.28-1.el8.noarch                233/1201 
  Verifying        : xkeyboard-config-2.28-1.el8.noarch                234/1201 
  Verifying        : yajl-2.1.0-10.el8.x86_64                          235/1201 
  Verifying        : yajl-2.1.0-10.el8.x86_64                          236/1201 
  Verifying        : NetworkManager-1:1.30.0-7.el8.x86_64              237/1201 
  Verifying        : NetworkManager-1:1.30.0-7.el8.x86_64              238/1201 
  Verifying        : NetworkManager-config-server-1:1.30.0-7.el8.no    239/1201 
  Verifying        : NetworkManager-config-server-1:1.30.0-7.el8.no    240/1201 
  Verifying        : NetworkManager-libnm-1:1.30.0-7.el8.x86_64        241/1201 
  Verifying        : NetworkManager-libnm-1:1.30.0-7.el8.x86_64        242/1201 
  Verifying        : NetworkManager-team-1:1.30.0-7.el8.x86_64         243/1201 
  Verifying        : NetworkManager-team-1:1.30.0-7.el8.x86_64         244/1201 
  Verifying        : NetworkManager-tui-1:1.30.0-7.el8.x86_64          245/1201 
  Verifying        : NetworkManager-tui-1:1.30.0-7.el8.x86_64          246/1201 
  Verifying        : adcli-0.8.2-9.el8.x86_64                          247/1201 
  Verifying        : adcli-0.8.2-9.el8.x86_64                          248/1201 
  Verifying        : alsa-sof-firmware-1.6.1-2.el8.noarch              249/1201 
  Verifying        : alsa-sof-firmware-1.6.1-2.el8.noarch              250/1201 
  Verifying        : at-3.1.20-11.el8.x86_64                           251/1201 
  Verifying        : at-3.1.20-11.el8.x86_64                           252/1201 
  Verifying        : attr-2.4.48-3.el8.x86_64                          253/1201 
  Verifying        : attr-2.4.48-3.el8.x86_64                          254/1201 
  Verifying        : authselect-1.2.2-2.el8.x86_64                     255/1201 
  Verifying        : authselect-1.2.2-2.el8.x86_64                     256/1201 
  Verifying        : authselect-libs-1.2.2-2.el8.x86_64                257/1201 
  Verifying        : authselect-libs-1.2.2-2.el8.x86_64                258/1201 
  Verifying        : avahi-libs-0.7-20.el8.x86_64                      259/1201 
  Verifying        : avahi-libs-0.7-20.el8.x86_64                      260/1201 
  Verifying        : basesystem-11-5.el8.noarch                        261/1201 
  Verifying        : basesystem-11-5.el8.noarch                        262/1201 
  Verifying        : bash-4.4.20-1.el8_4.x86_64                        263/1201 
  Verifying        : bash-4.4.20-1.el8_4.x86_64                        264/1201 
  Verifying        : bash-completion-1:2.7-5.el8.noarch                265/1201 
  Verifying        : bash-completion-1:2.7-5.el8.noarch                266/1201 
  Verifying        : bc-1.07.1-5.el8.x86_64                            267/1201 
  Verifying        : bc-1.07.1-5.el8.x86_64                            268/1201 
  Verifying        : bind-export-libs-32:9.11.26-4.el8_4.x86_64        269/1201 
  Verifying        : bind-export-libs-32:9.11.26-4.el8_4.x86_64        270/1201 
  Verifying        : binutils-2.30-93.el8.x86_64                       271/1201 
  Verifying        : binutils-2.30-93.el8.x86_64                       272/1201 
  Verifying        : biosdevname-0.7.3-2.el8.x86_64                    273/1201 
  Verifying        : biosdevname-0.7.3-2.el8.x86_64                    274/1201 
  Verifying        : blktrace-1.2.0-10.el8.x86_64                      275/1201 
  Verifying        : blktrace-1.2.0-10.el8.x86_64                      276/1201 
  Verifying        : bolt-0.9.1-1.el8.x86_64                           277/1201 
  Verifying        : bolt-0.9.1-1.el8.x86_64                           278/1201 
  Verifying        : brotli-1.0.6-3.el8.x86_64                         279/1201 
  Verifying        : brotli-1.0.6-3.el8.x86_64                         280/1201 
  Verifying        : bzip2-1.0.6-26.el8.x86_64                         281/1201 
  Verifying        : bzip2-1.0.6-26.el8.x86_64                         282/1201 
  Verifying        : bzip2-libs-1.0.6-26.el8.x86_64                    283/1201 
  Verifying        : bzip2-libs-1.0.6-26.el8.x86_64                    284/1201 
  Verifying        : c-ares-1.13.0-5.el8.x86_64                        285/1201 
  Verifying        : c-ares-1.13.0-5.el8.x86_64                        286/1201 
  Verifying        : ca-certificates-2020.2.41-80.0.el8_2.noarch       287/1201 
  Verifying        : ca-certificates-2020.2.41-80.0.el8_2.noarch       288/1201 
  Verifying        : checkpolicy-2.9-1.el8.x86_64                      289/1201 
  Verifying        : checkpolicy-2.9-1.el8.x86_64                      290/1201 
  Verifying        : chkconfig-1.13-2.el8.x86_64                       291/1201 
  Verifying        : chkconfig-1.13-2.el8.x86_64                       292/1201 
  Verifying        : chrony-3.5-2.el8.x86_64                           293/1201 
  Verifying        : chrony-3.5-2.el8.x86_64                           294/1201 
  Verifying        : cockpit-238.2-1.el8.x86_64                        295/1201 
  Verifying        : cockpit-238.2-1.el8.x86_64                        296/1201 
  Verifying        : cockpit-bridge-238.2-1.el8.x86_64                 297/1201 
  Verifying        : cockpit-bridge-238.2-1.el8.x86_64                 298/1201 
  Verifying        : cockpit-system-238.2-1.el8.noarch                 299/1201 
  Verifying        : cockpit-system-238.2-1.el8.noarch                 300/1201 
  Verifying        : cockpit-ws-238.2-1.el8.x86_64                     301/1201 
  Verifying        : cockpit-ws-238.2-1.el8.x86_64                     302/1201 
  Verifying        : coreutils-8.30-8.el8.x86_64                       303/1201 
  Verifying        : coreutils-8.30-8.el8.x86_64                       304/1201 
  Verifying        : coreutils-common-8.30-8.el8.x86_64                305/1201 
  Verifying        : coreutils-common-8.30-8.el8.x86_64                306/1201 
  Verifying        : cpio-2.12-10.el8.x86_64                           307/1201 
  Verifying        : cpio-2.12-10.el8.x86_64                           308/1201 
  Verifying        : cracklib-2.9.6-15.el8.x86_64                      309/1201 
  Verifying        : cracklib-2.9.6-15.el8.x86_64                      310/1201 
  Verifying        : cracklib-dicts-2.9.6-15.el8.x86_64                311/1201 
  Verifying        : cracklib-dicts-2.9.6-15.el8.x86_64                312/1201 
  Verifying        : cronie-1.5.2-4.el8.x86_64                         313/1201 
  Verifying        : cronie-1.5.2-4.el8.x86_64                         314/1201 
  Verifying        : cronie-anacron-1.5.2-4.el8.x86_64                 315/1201 
  Verifying        : cronie-anacron-1.5.2-4.el8.x86_64                 316/1201 
  Verifying        : crontabs-1.11-17.20190603git.el8.noarch           317/1201 
  Verifying        : crontabs-1.11-17.20190603git.el8.noarch           318/1201 
  Verifying        : crypto-policies-20210209-1.gitbfb6bed.el8_3.no    319/1201 
  Verifying        : crypto-policies-20210209-1.gitbfb6bed.el8_3.no    320/1201 
  Verifying        : crypto-policies-scripts-20210209-1.gitbfb6bed.    321/1201 
  Verifying        : crypto-policies-scripts-20210209-1.gitbfb6bed.    322/1201 
  Verifying        : cryptsetup-2.3.3-4.el8.x86_64                     323/1201 
  Verifying        : cryptsetup-2.3.3-4.el8.x86_64                     324/1201 
  Verifying        : cryptsetup-libs-2.3.3-4.el8.x86_64                325/1201 
  Verifying        : cryptsetup-libs-2.3.3-4.el8.x86_64                326/1201 
  Verifying        : cups-libs-1:2.2.6-38.el8.x86_64                   327/1201 
  Verifying        : cups-libs-1:2.2.6-38.el8.x86_64                   328/1201 
  Verifying        : curl-7.61.1-18.el8.x86_64                         329/1201 
  Verifying        : curl-7.61.1-18.el8.x86_64                         330/1201 
  Verifying        : cyrus-sasl-gssapi-2.1.27-5.el8.x86_64             331/1201 
  Verifying        : cyrus-sasl-gssapi-2.1.27-5.el8.x86_64             332/1201 
  Verifying        : cyrus-sasl-lib-2.1.27-5.el8.x86_64                333/1201 
  Verifying        : cyrus-sasl-lib-2.1.27-5.el8.x86_64                334/1201 
  Verifying        : cyrus-sasl-plain-2.1.27-5.el8.x86_64              335/1201 
  Verifying        : cyrus-sasl-plain-2.1.27-5.el8.x86_64              336/1201 
  Verifying        : dbus-1:1.12.8-12.el8_4.2.x86_64                   337/1201 
  Verifying        : dbus-1:1.12.8-12.el8_4.2.x86_64                   338/1201 
  Verifying        : dbus-common-1:1.12.8-12.el8_4.2.noarch            339/1201 
  Verifying        : dbus-common-1:1.12.8-12.el8_4.2.noarch            340/1201 
  Verifying        : dbus-daemon-1:1.12.8-12.el8_4.2.x86_64            341/1201 
  Verifying        : dbus-daemon-1:1.12.8-12.el8_4.2.x86_64            342/1201 
  Verifying        : dbus-glib-0.110-2.el8.x86_64                      343/1201 
  Verifying        : dbus-glib-0.110-2.el8.x86_64                      344/1201 
  Verifying        : dbus-libs-1:1.12.8-12.el8_4.2.x86_64              345/1201 
  Verifying        : dbus-libs-1:1.12.8-12.el8_4.2.x86_64              346/1201 
  Verifying        : dbus-tools-1:1.12.8-12.el8_4.2.x86_64             347/1201 
  Verifying        : dbus-tools-1:1.12.8-12.el8_4.2.x86_64             348/1201 
  Verifying        : dejavu-fonts-common-2.35-7.el8.noarch             349/1201 
  Verifying        : dejavu-fonts-common-2.35-7.el8.noarch             350/1201 
  Verifying        : dejavu-sans-mono-fonts-2.35-7.el8.noarch          351/1201 
  Verifying        : dejavu-sans-mono-fonts-2.35-7.el8.noarch          352/1201 
  Verifying        : device-mapper-8:1.02.175-5.el8.x86_64             353/1201 
  Verifying        : device-mapper-8:1.02.175-5.el8.x86_64             354/1201 
  Verifying        : device-mapper-event-8:1.02.175-5.el8.x86_64       355/1201 
  Verifying        : device-mapper-event-8:1.02.175-5.el8.x86_64       356/1201 
  Verifying        : device-mapper-event-libs-8:1.02.175-5.el8.x86_    357/1201 
  Verifying        : device-mapper-event-libs-8:1.02.175-5.el8.x86_    358/1201 
  Verifying        : device-mapper-libs-8:1.02.175-5.el8.x86_64        359/1201 
  Verifying        : device-mapper-libs-8:1.02.175-5.el8.x86_64        360/1201 
  Verifying        : device-mapper-multipath-0.8.4-10.el8.x86_64       361/1201 
  Verifying        : device-mapper-multipath-0.8.4-10.el8.x86_64       362/1201 
  Verifying        : device-mapper-multipath-libs-0.8.4-10.el8.x86_    363/1201 
  Verifying        : device-mapper-multipath-libs-0.8.4-10.el8.x86_    364/1201 
  Verifying        : device-mapper-persistent-data-0.8.5-4.el8.x86_    365/1201 
  Verifying        : device-mapper-persistent-data-0.8.5-4.el8.x86_    366/1201 
  Verifying        : diffutils-3.6-6.el8.x86_64                        367/1201 
  Verifying        : diffutils-3.6-6.el8.x86_64                        368/1201 
  Verifying        : dmidecode-1:3.2-8.el8.x86_64                      369/1201 
  Verifying        : dmidecode-1:3.2-8.el8.x86_64                      370/1201 
  Verifying        : dnf-4.4.2-11.el8.noarch                           371/1201 
  Verifying        : dnf-4.4.2-11.el8.noarch                           372/1201 
  Verifying        : dnf-data-4.4.2-11.el8.noarch                      373/1201 
  Verifying        : dnf-data-4.4.2-11.el8.noarch                      374/1201 
  Verifying        : dnf-plugins-core-4.0.18-4.el8.noarch              375/1201 
  Verifying        : dnf-plugins-core-4.0.18-4.el8.noarch              376/1201 
  Verifying        : dos2unix-7.4.0-3.el8.x86_64                       377/1201 
  Verifying        : dos2unix-7.4.0-3.el8.x86_64                       378/1201 
  Verifying        : dosfstools-4.1-6.el8.x86_64                       379/1201 
  Verifying        : dosfstools-4.1-6.el8.x86_64                       380/1201 
  Verifying        : dracut-049-135.git20210121.el8.x86_64             381/1201 
  Verifying        : dracut-049-135.git20210121.el8.x86_64             382/1201 
  Verifying        : dracut-config-rescue-049-135.git20210121.el8.x    383/1201 
  Verifying        : dracut-config-rescue-049-135.git20210121.el8.x    384/1201 
  Verifying        : dracut-network-049-135.git20210121.el8.x86_64     385/1201 
  Verifying        : dracut-network-049-135.git20210121.el8.x86_64     386/1201 
  Verifying        : dracut-squash-049-135.git20210121.el8.x86_64      387/1201 
  Verifying        : dracut-squash-049-135.git20210121.el8.x86_64      388/1201 
  Verifying        : ed-1.14.2-4.el8.x86_64                            389/1201 
  Verifying        : ed-1.14.2-4.el8.x86_64                            390/1201 
  Verifying        : elfutils-debuginfod-client-0.182-3.el8.x86_64     391/1201 
  Verifying        : elfutils-debuginfod-client-0.182-3.el8.x86_64     392/1201 
  Verifying        : elfutils-default-yama-scope-0.182-3.el8.noarch    393/1201 
  Verifying        : elfutils-default-yama-scope-0.182-3.el8.noarch    394/1201 
  Verifying        : elfutils-libelf-0.182-3.el8.x86_64                395/1201 
  Verifying        : elfutils-libelf-0.182-3.el8.x86_64                396/1201 
  Verifying        : elfutils-libs-0.182-3.el8.x86_64                  397/1201 
  Verifying        : elfutils-libs-0.182-3.el8.x86_64                  398/1201 
  Verifying        : emacs-filesystem-1:26.1-5.el8.noarch              399/1201 
  Verifying        : emacs-filesystem-1:26.1-5.el8.noarch              400/1201 
  Verifying        : ethtool-2:5.8-5.el8.x86_64                        401/1201 
  Verifying        : ethtool-2:5.8-5.el8.x86_64                        402/1201 
  Verifying        : expat-2.2.5-4.el8.x86_64                          403/1201 
  Verifying        : expat-2.2.5-4.el8.x86_64                          404/1201 
  Verifying        : file-5.33-16.el8_3.1.x86_64                       405/1201 
  Verifying        : file-5.33-16.el8_3.1.x86_64                       406/1201 
  Verifying        : file-libs-5.33-16.el8_3.1.x86_64                  407/1201 
  Verifying        : file-libs-5.33-16.el8_3.1.x86_64                  408/1201 
  Verifying        : filesystem-3.8-3.el8.x86_64                       409/1201 
  Verifying        : filesystem-3.8-3.el8.x86_64                       410/1201 
  Verifying        : findutils-1:4.6.0-20.el8.x86_64                   411/1201 
  Verifying        : findutils-1:4.6.0-20.el8.x86_64                   412/1201 
  Verifying        : firewalld-0.8.2-6.el8.noarch                      413/1201 
  Verifying        : firewalld-0.8.2-6.el8.noarch                      414/1201 
  Verifying        : firewalld-filesystem-0.8.2-6.el8.noarch           415/1201 
  Verifying        : firewalld-filesystem-0.8.2-6.el8.noarch           416/1201 
  Verifying        : fontconfig-2.13.1-3.el8.x86_64                    417/1201 
  Verifying        : fontconfig-2.13.1-3.el8.x86_64                    418/1201 
  Verifying        : fontpackages-filesystem-1.44-22.el8.noarch        419/1201 
  Verifying        : fontpackages-filesystem-1.44-22.el8.noarch        420/1201 
  Verifying        : freetype-2.9.1-4.el8_3.1.x86_64                   421/1201 
  Verifying        : freetype-2.9.1-4.el8_3.1.x86_64                   422/1201 
  Verifying        : fuse-common-3.2.1-12.el8.x86_64                   423/1201 
  Verifying        : fuse-common-3.2.1-12.el8.x86_64                   424/1201 
  Verifying        : fuse-libs-2.9.7-12.el8.x86_64                     425/1201 
  Verifying        : fuse-libs-2.9.7-12.el8.x86_64                     426/1201 
  Verifying        : fuse3-3.2.1-12.el8.x86_64                         427/1201 
  Verifying        : fuse3-3.2.1-12.el8.x86_64                         428/1201 
  Verifying        : fuse3-libs-3.2.1-12.el8.x86_64                    429/1201 
  Verifying        : fuse3-libs-3.2.1-12.el8.x86_64                    430/1201 
  Verifying        : gawk-4.2.1-2.el8.x86_64                           431/1201 
  Verifying        : gawk-4.2.1-2.el8.x86_64                           432/1201 
  Verifying        : gdbm-1:1.18-1.el8.x86_64                          433/1201 
  Verifying        : gdbm-1:1.18-1.el8.x86_64                          434/1201 
  Verifying        : gdbm-libs-1:1.18-1.el8.x86_64                     435/1201 
  Verifying        : gdbm-libs-1:1.18-1.el8.x86_64                     436/1201 
  Verifying        : gdisk-1.0.3-6.el8.x86_64                          437/1201 
  Verifying        : gdisk-1.0.3-6.el8.x86_64                          438/1201 
  Verifying        : gdk-pixbuf2-2.36.12-5.el8.x86_64                  439/1201 
  Verifying        : gdk-pixbuf2-2.36.12-5.el8.x86_64                  440/1201 
  Verifying        : gettext-0.19.8.1-17.el8.x86_64                    441/1201 
  Verifying        : gettext-0.19.8.1-17.el8.x86_64                    442/1201 
  Verifying        : gettext-libs-0.19.8.1-17.el8.x86_64               443/1201 
  Verifying        : gettext-libs-0.19.8.1-17.el8.x86_64               444/1201 
  Verifying        : glib-networking-2.56.1-1.1.el8.x86_64             445/1201 
  Verifying        : glib-networking-2.56.1-1.1.el8.x86_64             446/1201 
  Verifying        : glib2-2.56.4-10.el8_4.x86_64                      447/1201 
  Verifying        : glib2-2.56.4-10.el8_4.x86_64                      448/1201 
  Verifying        : glibc-2.28-151.el8.x86_64                         449/1201 
  Verifying        : glibc-2.28-151.el8.x86_64                         450/1201 
  Verifying        : glibc-common-2.28-151.el8.x86_64                  451/1201 
  Verifying        : glibc-common-2.28-151.el8.x86_64                  452/1201 
  Verifying        : glibc-langpack-en-2.28-151.el8.x86_64             453/1201 
  Verifying        : glibc-langpack-en-2.28-151.el8.x86_64             454/1201 
  Verifying        : gmp-1:6.1.2-10.el8.x86_64                         455/1201 
  Verifying        : gmp-1:6.1.2-10.el8.x86_64                         456/1201 
  Verifying        : gnupg2-2.2.20-2.el8.x86_64                        457/1201 
  Verifying        : gnupg2-2.2.20-2.el8.x86_64                        458/1201 
  Verifying        : gnupg2-smime-2.2.20-2.el8.x86_64                  459/1201 
  Verifying        : gnupg2-smime-2.2.20-2.el8.x86_64                  460/1201 
  Verifying        : gnutls-3.6.14-8.el8_3.x86_64                      461/1201 
  Verifying        : gnutls-3.6.14-8.el8_3.x86_64                      462/1201 
  Verifying        : gobject-introspection-1.56.1-1.el8.x86_64         463/1201 
  Verifying        : gobject-introspection-1.56.1-1.el8.x86_64         464/1201 
  Verifying        : gpgme-1.13.1-7.el8.x86_64                         465/1201 
  Verifying        : gpgme-1.13.1-7.el8.x86_64                         466/1201 
  Verifying        : grep-3.1-6.el8.x86_64                             467/1201 
  Verifying        : grep-3.1-6.el8.x86_64                             468/1201 
  Verifying        : groff-base-1.22.3-18.el8.x86_64                   469/1201 
  Verifying        : groff-base-1.22.3-18.el8.x86_64                   470/1201 
  Verifying        : grub2-common-1:2.02-99.el8.noarch                 471/1201 
  Verifying        : grub2-common-1:2.02-99.el8.noarch                 472/1201 
  Verifying        : grub2-pc-1:2.02-99.el8.x86_64                     473/1201 
  Verifying        : grub2-pc-1:2.02-99.el8.x86_64                     474/1201 
  Verifying        : grub2-pc-modules-1:2.02-99.el8.noarch             475/1201 
  Verifying        : grub2-pc-modules-1:2.02-99.el8.noarch             476/1201 
  Verifying        : grub2-tools-1:2.02-99.el8.x86_64                  477/1201 
  Verifying        : grub2-tools-1:2.02-99.el8.x86_64                  478/1201 
  Verifying        : grub2-tools-extra-1:2.02-99.el8.x86_64            479/1201 
  Verifying        : grub2-tools-extra-1:2.02-99.el8.x86_64            480/1201 
  Verifying        : grub2-tools-minimal-1:2.02-99.el8.x86_64          481/1201 
  Verifying        : grub2-tools-minimal-1:2.02-99.el8.x86_64          482/1201 
  Verifying        : grubby-8.40-41.el8.x86_64                         483/1201 
  Verifying        : grubby-8.40-41.el8.x86_64                         484/1201 
  Verifying        : gsettings-desktop-schemas-3.32.0-5.el8.x86_64     485/1201 
  Verifying        : gsettings-desktop-schemas-3.32.0-5.el8.x86_64     486/1201 
  Verifying        : gzip-1.9-12.el8.x86_64                            487/1201 
  Verifying        : gzip-1.9-12.el8.x86_64                            488/1201 
  Verifying        : hardlink-1:1.3-6.el8.x86_64                       489/1201 
  Verifying        : hardlink-1:1.3-6.el8.x86_64                       490/1201 
  Verifying        : hdparm-9.54-3.el8.x86_64                          491/1201 
  Verifying        : hdparm-9.54-3.el8.x86_64                          492/1201 
  Verifying        : hostname-3.20-6.el8.x86_64                        493/1201 
  Verifying        : hostname-3.20-6.el8.x86_64                        494/1201 
  Verifying        : hwdata-0.314-8.8.el8.noarch                       495/1201 
  Verifying        : hwdata-0.314-8.8.el8.noarch                       496/1201 
  Verifying        : ima-evm-utils-1.3.2-12.el8.x86_64                 497/1201 
  Verifying        : ima-evm-utils-1.3.2-12.el8.x86_64                 498/1201 
  Verifying        : info-6.5-6.el8.x86_64                             499/1201 
  Verifying        : info-6.5-6.el8.x86_64                             500/1201 
  Verifying        : initscripts-10.00.15-1.el8.x86_64                 501/1201 
  Verifying        : initscripts-10.00.15-1.el8.x86_64                 502/1201 
  Verifying        : ipcalc-0.2.4-4.el8.x86_64                         503/1201 
  Verifying        : ipcalc-0.2.4-4.el8.x86_64                         504/1201 
  Verifying        : iproute-5.9.0-4.el8.x86_64                        505/1201 
  Verifying        : iproute-5.9.0-4.el8.x86_64                        506/1201 
  Verifying        : iprutils-2.4.19-1.el8.x86_64                      507/1201 
  Verifying        : iprutils-2.4.19-1.el8.x86_64                      508/1201 
  Verifying        : ipset-7.1-1.el8.x86_64                            509/1201 
  Verifying        : ipset-7.1-1.el8.x86_64                            510/1201 
  Verifying        : ipset-libs-7.1-1.el8.x86_64                       511/1201 
  Verifying        : ipset-libs-7.1-1.el8.x86_64                       512/1201 
  Verifying        : iptables-1.8.4-17.el8.x86_64                      513/1201 
  Verifying        : iptables-1.8.4-17.el8.x86_64                      514/1201 
  Verifying        : iptables-ebtables-1.8.4-17.el8.x86_64             515/1201 
  Verifying        : iptables-ebtables-1.8.4-17.el8.x86_64             516/1201 
  Verifying        : iptables-libs-1.8.4-17.el8.x86_64                 517/1201 
  Verifying        : iptables-libs-1.8.4-17.el8.x86_64                 518/1201 
  Verifying        : iptstate-2.2.6-6.el8.x86_64                       519/1201 
  Verifying        : iptstate-2.2.6-6.el8.x86_64                       520/1201 
  Verifying        : iputils-20180629-7.el8.x86_64                     521/1201 
  Verifying        : iputils-20180629-7.el8.x86_64                     522/1201 
  Verifying        : irqbalance-2:1.4.0-6.el8.x86_64                   523/1201 
  Verifying        : irqbalance-2:1.4.0-6.el8.x86_64                   524/1201 
  Verifying        : iscsi-initiator-utils-6.2.1.2-1.gita8fcb37.el8    525/1201 
  Verifying        : iscsi-initiator-utils-6.2.1.2-1.gita8fcb37.el8    526/1201 
  Verifying        : iscsi-initiator-utils-iscsiuio-6.2.1.2-1.gita8    527/1201 
  Verifying        : iscsi-initiator-utils-iscsiuio-6.2.1.2-1.gita8    528/1201 
  Verifying        : isns-utils-libs-0.99-1.el8.x86_64                 529/1201 
  Verifying        : isns-utils-libs-0.99-1.el8.x86_64                 530/1201 
  Verifying        : iwl100-firmware-39.31.5.1-102.el8.1.noarch        531/1201 
  Verifying        : iwl100-firmware-39.31.5.1-102.el8.1.noarch        532/1201 
  Verifying        : iwl1000-firmware-1:39.31.5.1-102.el8.1.noarch     533/1201 
  Verifying        : iwl1000-firmware-1:39.31.5.1-102.el8.1.noarch     534/1201 
  Verifying        : iwl105-firmware-18.168.6.1-102.el8.1.noarch       535/1201 
  Verifying        : iwl105-firmware-18.168.6.1-102.el8.1.noarch       536/1201 
  Verifying        : iwl135-firmware-18.168.6.1-102.el8.1.noarch       537/1201 
  Verifying        : iwl135-firmware-18.168.6.1-102.el8.1.noarch       538/1201 
  Verifying        : iwl2000-firmware-18.168.6.1-102.el8.1.noarch      539/1201 
  Verifying        : iwl2000-firmware-18.168.6.1-102.el8.1.noarch      540/1201 
  Verifying        : iwl2030-firmware-18.168.6.1-102.el8.1.noarch      541/1201 
  Verifying        : iwl2030-firmware-18.168.6.1-102.el8.1.noarch      542/1201 
  Verifying        : iwl3160-firmware-1:25.30.13.0-102.el8.1.noarch    543/1201 
  Verifying        : iwl3160-firmware-1:25.30.13.0-102.el8.1.noarch    544/1201 
  Verifying        : iwl5000-firmware-8.83.5.1_1-102.el8.1.noarch      545/1201 
  Verifying        : iwl5000-firmware-8.83.5.1_1-102.el8.1.noarch      546/1201 
  Verifying        : iwl5150-firmware-8.24.2.2-102.el8.1.noarch        547/1201 
  Verifying        : iwl5150-firmware-8.24.2.2-102.el8.1.noarch        548/1201 
  Verifying        : iwl6000-firmware-9.221.4.1-102.el8.1.noarch       549/1201 
  Verifying        : iwl6000-firmware-9.221.4.1-102.el8.1.noarch       550/1201 
  Verifying        : iwl6000g2a-firmware-18.168.6.1-102.el8.1.noarc    551/1201 
  Verifying        : iwl6000g2a-firmware-18.168.6.1-102.el8.1.noarc    552/1201 
  Verifying        : iwl6000g2b-firmware-18.168.6.1-102.el8.1.noarc    553/1201 
  Verifying        : iwl6000g2b-firmware-18.168.6.1-102.el8.1.noarc    554/1201 
  Verifying        : iwl6050-firmware-41.28.5.1-102.el8.1.noarch       555/1201 
  Verifying        : iwl6050-firmware-41.28.5.1-102.el8.1.noarch       556/1201 
  Verifying        : iwl7260-firmware-1:25.30.13.0-102.el8.1.noarch    557/1201 
  Verifying        : iwl7260-firmware-1:25.30.13.0-102.el8.1.noarch    558/1201 
  Verifying        : jansson-2.11-3.el8.x86_64                         559/1201 
  Verifying        : jansson-2.11-3.el8.x86_64                         560/1201 
  Verifying        : json-c-0.13.1-0.4.el8.x86_64                      561/1201 
  Verifying        : json-c-0.13.1-0.4.el8.x86_64                      562/1201 
  Verifying        : json-glib-1.4.4-1.el8.x86_64                      563/1201 
  Verifying        : json-glib-1.4.4-1.el8.x86_64                      564/1201 
  Verifying        : kbd-2.0.4-10.el8.x86_64                           565/1201 
  Verifying        : kbd-2.0.4-10.el8.x86_64                           566/1201 
  Verifying        : kbd-legacy-2.0.4-10.el8.noarch                    567/1201 
  Verifying        : kbd-legacy-2.0.4-10.el8.noarch                    568/1201 
  Verifying        : kbd-misc-2.0.4-10.el8.noarch                      569/1201 
  Verifying        : kbd-misc-2.0.4-10.el8.noarch                      570/1201 
  Verifying        : kexec-tools-2.0.20-46.el8.x86_64                  571/1201 
  Verifying        : kexec-tools-2.0.20-46.el8.x86_64                  572/1201 
  Verifying        : keyutils-libs-1.5.10-6.el8.x86_64                 573/1201 
  Verifying        : keyutils-libs-1.5.10-6.el8.x86_64                 574/1201 
  Verifying        : kmod-25-17.el8.x86_64                             575/1201 
  Verifying        : kmod-25-17.el8.x86_64                             576/1201 
  Verifying        : kmod-kvdo-6.2.4.26-77.el8.x86_64                  577/1201 
  Verifying        : kmod-kvdo-6.2.4.26-77.el8.x86_64                  578/1201 
  Verifying        : kmod-libs-25-17.el8.x86_64                        579/1201 
  Verifying        : kmod-libs-25-17.el8.x86_64                        580/1201 
  Verifying        : kpartx-0.8.4-10.el8.x86_64                        581/1201 
  Verifying        : kpartx-0.8.4-10.el8.x86_64                        582/1201 
  Verifying        : kpatch-0.9.2-3.el8.noarch                         583/1201 
  Verifying        : kpatch-0.9.2-3.el8.noarch                         584/1201 
  Verifying        : kpatch-dnf-0.2-3.el8.noarch                       585/1201 
  Verifying        : kpatch-dnf-0.2-3.el8.noarch                       586/1201 
  Verifying        : krb5-libs-1.18.2-8.el8.x86_64                     587/1201 
  Verifying        : krb5-libs-1.18.2-8.el8.x86_64                     588/1201 
  Verifying        : ledmon-0.95-1.el8.x86_64                          589/1201 
  Verifying        : ledmon-0.95-1.el8.x86_64                          590/1201 
  Verifying        : less-530-1.el8.x86_64                             591/1201 
  Verifying        : less-530-1.el8.x86_64                             592/1201 
  Verifying        : libaio-0.3.112-1.el8.x86_64                       593/1201 
  Verifying        : libaio-0.3.112-1.el8.x86_64                       594/1201 
  Verifying        : libappstream-glib-0.7.14-3.el8.x86_64             595/1201 
  Verifying        : libappstream-glib-0.7.14-3.el8.x86_64             596/1201 
  Verifying        : libarchive-3.3.3-1.el8.x86_64                     597/1201 
  Verifying        : libarchive-3.3.3-1.el8.x86_64                     598/1201 
  Verifying        : libassuan-2.5.1-3.el8.x86_64                      599/1201 
  Verifying        : libassuan-2.5.1-3.el8.x86_64                      600/1201 
  Verifying        : libattr-2.4.48-3.el8.x86_64                       601/1201 
  Verifying        : libattr-2.4.48-3.el8.x86_64                       602/1201 
  Verifying        : libbasicobjects-0.1.1-39.el8.x86_64               603/1201 
  Verifying        : libbasicobjects-0.1.1-39.el8.x86_64               604/1201 
  Verifying        : libblkid-2.32.1-27.el8.x86_64                     605/1201 
  Verifying        : libblkid-2.32.1-27.el8.x86_64                     606/1201 
  Verifying        : libcap-2.26-4.el8.x86_64                          607/1201 
  Verifying        : libcap-2.26-4.el8.x86_64                          608/1201 
  Verifying        : libcap-ng-0.7.9-5.el8.x86_64                      609/1201 
  Verifying        : libcap-ng-0.7.9-5.el8.x86_64                      610/1201 
  Verifying        : libcollection-0.7.0-39.el8.x86_64                 611/1201 
  Verifying        : libcollection-0.7.0-39.el8.x86_64                 612/1201 
  Verifying        : libcomps-0.1.11-5.el8.x86_64                      613/1201 
  Verifying        : libcomps-0.1.11-5.el8.x86_64                      614/1201 
  Verifying        : libconfig-1.5-9.el8.x86_64                        615/1201 
  Verifying        : libconfig-1.5-9.el8.x86_64                        616/1201 
  Verifying        : libcroco-0.6.12-4.el8_2.1.x86_64                  617/1201 
  Verifying        : libcroco-0.6.12-4.el8_2.1.x86_64                  618/1201 
  Verifying        : libcurl-7.61.1-18.el8.x86_64                      619/1201 
  Verifying        : libcurl-7.61.1-18.el8.x86_64                      620/1201 
  Verifying        : libdaemon-0.14-15.el8.x86_64                      621/1201 
  Verifying        : libdaemon-0.14-15.el8.x86_64                      622/1201 
  Verifying        : libdb-5.3.28-40.el8.x86_64                        623/1201 
  Verifying        : libdb-5.3.28-40.el8.x86_64                        624/1201 
  Verifying        : libdb-utils-5.3.28-40.el8.x86_64                  625/1201 
  Verifying        : libdb-utils-5.3.28-40.el8.x86_64                  626/1201 
  Verifying        : libdhash-0.5.0-39.el8.x86_64                      627/1201 
  Verifying        : libdhash-0.5.0-39.el8.x86_64                      628/1201 
  Verifying        : libdnf-0.55.0-7.el8.x86_64                        629/1201 
  Verifying        : libdnf-0.55.0-7.el8.x86_64                        630/1201 
  Verifying        : libedit-3.1-23.20170329cvs.el8.x86_64             631/1201 
  Verifying        : libedit-3.1-23.20170329cvs.el8.x86_64             632/1201 
  Verifying        : libertas-usb8388-firmware-2:20201218-102.git05    633/1201 
  Verifying        : libertas-usb8388-firmware-2:20201218-102.git05    634/1201 
  Verifying        : libevent-2.1.8-5.el8.x86_64                       635/1201 
  Verifying        : libevent-2.1.8-5.el8.x86_64                       636/1201 
  Verifying        : libfdisk-2.32.1-27.el8.x86_64                     637/1201 
  Verifying        : libfdisk-2.32.1-27.el8.x86_64                     638/1201 
  Verifying        : libffi-3.1-22.el8.x86_64                          639/1201 
  Verifying        : libffi-3.1-22.el8.x86_64                          640/1201 
  Verifying        : libgcc-8.4.1-1.el8.x86_64                         641/1201 
  Verifying        : libgcc-8.4.1-1.el8.x86_64                         642/1201 
  Verifying        : libgcrypt-1.8.5-4.el8.x86_64                      643/1201 
  Verifying        : libgcrypt-1.8.5-4.el8.x86_64                      644/1201 
  Verifying        : libgomp-8.4.1-1.el8.x86_64                        645/1201 
  Verifying        : libgomp-8.4.1-1.el8.x86_64                        646/1201 
  Verifying        : libgpg-error-1.31-1.el8.x86_64                    647/1201 
  Verifying        : libgpg-error-1.31-1.el8.x86_64                    648/1201 
  Verifying        : libgudev-232-4.el8.x86_64                         649/1201 
  Verifying        : libgudev-232-4.el8.x86_64                         650/1201 
  Verifying        : libgusb-0.3.0-1.el8.x86_64                        651/1201 
  Verifying        : libgusb-0.3.0-1.el8.x86_64                        652/1201 
  Verifying        : libibverbs-32.0-4.el8.x86_64                      653/1201 
  Verifying        : libibverbs-32.0-4.el8.x86_64                      654/1201 
  Verifying        : libicu-60.3-2.el8_1.x86_64                        655/1201 
  Verifying        : libicu-60.3-2.el8_1.x86_64                        656/1201 
  Verifying        : libidn2-2.2.0-1.el8.x86_64                        657/1201 
  Verifying        : libidn2-2.2.0-1.el8.x86_64                        658/1201 
  Verifying        : libini_config-1.3.1-39.el8.x86_64                 659/1201 
  Verifying        : libini_config-1.3.1-39.el8.x86_64                 660/1201 
  Verifying        : libipa_hbac-2.4.0-9.el8.x86_64                    661/1201 
  Verifying        : libipa_hbac-2.4.0-9.el8.x86_64                    662/1201 
  Verifying        : libkcapi-1.2.0-2.el8.x86_64                       663/1201 
  Verifying        : libkcapi-1.2.0-2.el8.x86_64                       664/1201 
  Verifying        : libkcapi-hmaccalc-1.2.0-2.el8.x86_64              665/1201 
  Verifying        : libkcapi-hmaccalc-1.2.0-2.el8.x86_64              666/1201 
  Verifying        : libksba-1.3.5-7.el8.x86_64                        667/1201 
  Verifying        : libksba-1.3.5-7.el8.x86_64                        668/1201 
  Verifying        : libldb-2.2.0-2.el8.x86_64                         669/1201 
  Verifying        : libldb-2.2.0-2.el8.x86_64                         670/1201 
  Verifying        : libmetalink-0.1.3-7.el8.x86_64                    671/1201 
  Verifying        : libmetalink-0.1.3-7.el8.x86_64                    672/1201 
  Verifying        : libmnl-1.0.4-6.el8.x86_64                         673/1201 
  Verifying        : libmnl-1.0.4-6.el8.x86_64                         674/1201 
  Verifying        : libmodman-2.0.1-17.el8.x86_64                     675/1201 
  Verifying        : libmodman-2.0.1-17.el8.x86_64                     676/1201 
  Verifying        : libmodulemd-2.9.4-2.el8.x86_64                    677/1201 
  Verifying        : libmodulemd-2.9.4-2.el8.x86_64                    678/1201 
  Verifying        : libmount-2.32.1-27.el8.x86_64                     679/1201 
  Verifying        : libmount-2.32.1-27.el8.x86_64                     680/1201 
  Verifying        : libndp-1.7-5.el8.x86_64                           681/1201 
  Verifying        : libndp-1.7-5.el8.x86_64                           682/1201 
  Verifying        : libnetfilter_conntrack-1.0.6-5.el8.x86_64         683/1201 
  Verifying        : libnetfilter_conntrack-1.0.6-5.el8.x86_64         684/1201 
  Verifying        : libnfnetlink-1.0.1-13.el8.x86_64                  685/1201 
  Verifying        : libnfnetlink-1.0.1-13.el8.x86_64                  686/1201 
  Verifying        : libnfsidmap-1:2.3.3-41.el8.x86_64                 687/1201 
  Verifying        : libnfsidmap-1:2.3.3-41.el8.x86_64                 688/1201 
  Verifying        : libnftnl-1.1.5-4.el8.x86_64                       689/1201 
  Verifying        : libnftnl-1.1.5-4.el8.x86_64                       690/1201 
  Verifying        : libnl3-3.5.0-1.el8.x86_64                         691/1201 
  Verifying        : libnl3-3.5.0-1.el8.x86_64                         692/1201 
  Verifying        : libnl3-cli-3.5.0-1.el8.x86_64                     693/1201 
  Verifying        : libnl3-cli-3.5.0-1.el8.x86_64                     694/1201 
  Verifying        : libnsl2-1.2.0-2.20180605git4a062cf.el8.x86_64     695/1201 
  Verifying        : libnsl2-1.2.0-2.20180605git4a062cf.el8.x86_64     696/1201 
  Verifying        : libpath_utils-0.2.1-39.el8.x86_64                 697/1201 
  Verifying        : libpath_utils-0.2.1-39.el8.x86_64                 698/1201 
  Verifying        : libpcap-14:1.9.1-5.el8.x86_64                     699/1201 
  Verifying        : libpcap-14:1.9.1-5.el8.x86_64                     700/1201 
  Verifying        : libpipeline-1.5.0-2.el8.x86_64                    701/1201 
  Verifying        : libpipeline-1.5.0-2.el8.x86_64                    702/1201 
  Verifying        : libpkgconf-1.4.2-1.el8.x86_64                     703/1201 
  Verifying        : libpkgconf-1.4.2-1.el8.x86_64                     704/1201 
  Verifying        : libpng-2:1.6.34-5.el8.x86_64                      705/1201 
  Verifying        : libpng-2:1.6.34-5.el8.x86_64                      706/1201 
  Verifying        : libproxy-0.4.15-5.2.el8.x86_64                    707/1201 
  Verifying        : libproxy-0.4.15-5.2.el8.x86_64                    708/1201 
  Verifying        : libpsl-0.20.2-6.el8.x86_64                        709/1201 
  Verifying        : libpsl-0.20.2-6.el8.x86_64                        710/1201 
  Verifying        : libpwquality-1.4.4-3.el8.x86_64                   711/1201 
  Verifying        : libpwquality-1.4.4-3.el8.x86_64                   712/1201 
  Verifying        : libref_array-0.1.5-39.el8.x86_64                  713/1201 
  Verifying        : libref_array-0.1.5-39.el8.x86_64                  714/1201 
  Verifying        : librepo-1.12.0-3.el8.x86_64                       715/1201 
  Verifying        : librepo-1.12.0-3.el8.x86_64                       716/1201 
  Verifying        : libseccomp-2.5.1-1.el8.x86_64                     717/1201 
  Verifying        : libseccomp-2.5.1-1.el8.x86_64                     718/1201 
  Verifying        : libsecret-0.18.6-1.el8.x86_64                     719/1201 
  Verifying        : libsecret-0.18.6-1.el8.x86_64                     720/1201 
  Verifying        : libselinux-2.9-5.el8.x86_64                       721/1201 
  Verifying        : libselinux-2.9-5.el8.x86_64                       722/1201 
  Verifying        : libselinux-utils-2.9-5.el8.x86_64                 723/1201 
  Verifying        : libselinux-utils-2.9-5.el8.x86_64                 724/1201 
  Verifying        : libsemanage-2.9-6.el8.x86_64                      725/1201 
  Verifying        : libsemanage-2.9-6.el8.x86_64                      726/1201 
  Verifying        : libsepol-2.9-2.el8.x86_64                         727/1201 
  Verifying        : libsepol-2.9-2.el8.x86_64                         728/1201 
  Verifying        : libsigsegv-2.11-5.el8.x86_64                      729/1201 
  Verifying        : libsigsegv-2.11-5.el8.x86_64                      730/1201 
  Verifying        : libsmartcols-2.32.1-27.el8.x86_64                 731/1201 
  Verifying        : libsmartcols-2.32.1-27.el8.x86_64                 732/1201 
  Verifying        : libsmbclient-4.13.3-3.el8.x86_64                  733/1201 
  Verifying        : libsmbclient-4.13.3-3.el8.x86_64                  734/1201 
  Verifying        : libsolv-0.7.16-2.el8.x86_64                       735/1201 
  Verifying        : libsolv-0.7.16-2.el8.x86_64                       736/1201 
  Verifying        : libsoup-2.62.3-2.el8.x86_64                       737/1201 
  Verifying        : libsoup-2.62.3-2.el8.x86_64                       738/1201 
  Verifying        : libssh-0.9.4-2.el8.x86_64                         739/1201 
  Verifying        : libssh-0.9.4-2.el8.x86_64                         740/1201 
  Verifying        : libssh-config-0.9.4-2.el8.noarch                  741/1201 
  Verifying        : libssh-config-0.9.4-2.el8.noarch                  742/1201 
  Verifying        : libsss_autofs-2.4.0-9.el8.x86_64                  743/1201 
  Verifying        : libsss_autofs-2.4.0-9.el8.x86_64                  744/1201 
  Verifying        : libsss_certmap-2.4.0-9.el8.x86_64                 745/1201 
  Verifying        : libsss_certmap-2.4.0-9.el8.x86_64                 746/1201 
  Verifying        : libsss_idmap-2.4.0-9.el8.x86_64                   747/1201 
  Verifying        : libsss_idmap-2.4.0-9.el8.x86_64                   748/1201 
  Verifying        : libsss_nss_idmap-2.4.0-9.el8.x86_64               749/1201 
  Verifying        : libsss_nss_idmap-2.4.0-9.el8.x86_64               750/1201 
  Verifying        : libsss_sudo-2.4.0-9.el8.x86_64                    751/1201 
  Verifying        : libsss_sudo-2.4.0-9.el8.x86_64                    752/1201 
  Verifying        : libstdc++-8.4.1-1.el8.x86_64                      753/1201 
  Verifying        : libstdc++-8.4.1-1.el8.x86_64                      754/1201 
  Verifying        : libstemmer-0-10.585svn.el8.x86_64                 755/1201 
  Verifying        : libstemmer-0-10.585svn.el8.x86_64                 756/1201 
  Verifying        : libstoragemgmt-1.8.7-1.el8.x86_64                 757/1201 
  Verifying        : libstoragemgmt-1.8.7-1.el8.x86_64                 758/1201 
  Verifying        : libsysfs-2.1.0-24.el8.x86_64                      759/1201 
  Verifying        : libsysfs-2.1.0-24.el8.x86_64                      760/1201 
  Verifying        : libtalloc-2.3.1-2.el8.x86_64                      761/1201 
  Verifying        : libtalloc-2.3.1-2.el8.x86_64                      762/1201 
  Verifying        : libtasn1-4.13-3.el8.x86_64                        763/1201 
  Verifying        : libtasn1-4.13-3.el8.x86_64                        764/1201 
  Verifying        : libtdb-1.4.3-1.el8.x86_64                         765/1201 
  Verifying        : libtdb-1.4.3-1.el8.x86_64                         766/1201 
  Verifying        : libteam-1.31-2.el8.x86_64                         767/1201 
  Verifying        : libteam-1.31-2.el8.x86_64                         768/1201 
  Verifying        : libtevent-0.10.2-2.el8.x86_64                     769/1201 
  Verifying        : libtevent-0.10.2-2.el8.x86_64                     770/1201 
  Verifying        : libtirpc-1.1.4-4.el8.x86_64                       771/1201 
  Verifying        : libtirpc-1.1.4-4.el8.x86_64                       772/1201 
  Verifying        : libunistring-0.9.9-3.el8.x86_64                   773/1201 
  Verifying        : libunistring-0.9.9-3.el8.x86_64                   774/1201 
  Verifying        : libusbx-1.0.23-4.el8.x86_64                       775/1201 
  Verifying        : libusbx-1.0.23-4.el8.x86_64                       776/1201 
  Verifying        : libuser-0.62-23.el8.x86_64                        777/1201 
  Verifying        : libuser-0.62-23.el8.x86_64                        778/1201 
  Verifying        : libutempter-1.1.6-14.el8.x86_64                   779/1201 
  Verifying        : libutempter-1.1.6-14.el8.x86_64                   780/1201 
  Verifying        : libuuid-2.32.1-27.el8.x86_64                      781/1201 
  Verifying        : libuuid-2.32.1-27.el8.x86_64                      782/1201 
  Verifying        : libverto-0.3.0-5.el8.x86_64                       783/1201 
  Verifying        : libverto-0.3.0-5.el8.x86_64                       784/1201 
  Verifying        : libwbclient-4.13.3-3.el8.x86_64                   785/1201 
  Verifying        : libwbclient-4.13.3-3.el8.x86_64                   786/1201 
  Verifying        : libxcrypt-4.1.1-4.el8.x86_64                      787/1201 
  Verifying        : libxcrypt-4.1.1-4.el8.x86_64                      788/1201 
  Verifying        : libxml2-2.9.7-9.el8.x86_64                        789/1201 
  Verifying        : libxml2-2.9.7-9.el8.x86_64                        790/1201 
  Verifying        : libxslt-1.1.32-6.el8.x86_64                       791/1201 
  Verifying        : libxslt-1.1.32-6.el8.x86_64                       792/1201 
  Verifying        : libyaml-0.1.7-5.el8.x86_64                        793/1201 
  Verifying        : libyaml-0.1.7-5.el8.x86_64                        794/1201 
  Verifying        : libzstd-1.4.4-1.el8.x86_64                        795/1201 
  Verifying        : libzstd-1.4.4-1.el8.x86_64                        796/1201 
  Verifying        : linux-firmware-20201218-102.git05789708.el8.no    797/1201 
  Verifying        : linux-firmware-20201218-102.git05789708.el8.no    798/1201 
  Verifying        : lmdb-libs-0.9.24-1.el8.x86_64                     799/1201 
  Verifying        : lmdb-libs-0.9.24-1.el8.x86_64                     800/1201 
  Verifying        : logrotate-3.14.0-4.el8.x86_64                     801/1201 
  Verifying        : logrotate-3.14.0-4.el8.x86_64                     802/1201 
  Verifying        : lshw-B.02.19.2-5.el8.x86_64                       803/1201 
  Verifying        : lshw-B.02.19.2-5.el8.x86_64                       804/1201 
  Verifying        : lsof-4.93.2-1.el8.x86_64                          805/1201 
  Verifying        : lsof-4.93.2-1.el8.x86_64                          806/1201 
  Verifying        : lsscsi-0.32-2.el8.x86_64                          807/1201 
  Verifying        : lsscsi-0.32-2.el8.x86_64                          808/1201 
  Verifying        : lua-libs-5.3.4-11.el8.x86_64                      809/1201 
  Verifying        : lua-libs-5.3.4-11.el8.x86_64                      810/1201 
  Verifying        : lvm2-8:2.03.11-5.el8.x86_64                       811/1201 
  Verifying        : lvm2-8:2.03.11-5.el8.x86_64                       812/1201 
  Verifying        : lvm2-libs-8:2.03.11-5.el8.x86_64                  813/1201 
  Verifying        : lvm2-libs-8:2.03.11-5.el8.x86_64                  814/1201 
  Verifying        : lz4-libs-1.8.3-2.el8.x86_64                       815/1201 
  Verifying        : lz4-libs-1.8.3-2.el8.x86_64                       816/1201 
  Verifying        : lzo-2.08-14.el8.x86_64                            817/1201 
  Verifying        : lzo-2.08-14.el8.x86_64                            818/1201 
  Verifying        : mailcap-2.1.48-3.el8.noarch                       819/1201 
  Verifying        : mailcap-2.1.48-3.el8.noarch                       820/1201 
  Verifying        : man-db-2.7.6.1-17.el8.x86_64                      821/1201 
  Verifying        : man-db-2.7.6.1-17.el8.x86_64                      822/1201 
  Verifying        : man-pages-4.15-6.el8.x86_64                       823/1201 
  Verifying        : man-pages-4.15-6.el8.x86_64                       824/1201 
  Verifying        : mcelog-3:173-0.el8.x86_64                         825/1201 
  Verifying        : mcelog-3:173-0.el8.x86_64                         826/1201 
  Verifying        : mdadm-4.1-15.el8.x86_64                           827/1201 
  Verifying        : mdadm-4.1-15.el8.x86_64                           828/1201 
  Verifying        : memstrack-0.1.11-1.el8.x86_64                     829/1201 
  Verifying        : memstrack-0.1.11-1.el8.x86_64                     830/1201 
  Verifying        : microcode_ctl-4:20210216-1.20210525.1.el8_4.x8    831/1201 
  Verifying        : microcode_ctl-4:20210216-1.20210525.1.el8_4.x8    832/1201 
  Verifying        : mlocate-0.26-20.el8.x86_64                        833/1201 
  Verifying        : mlocate-0.26-20.el8.x86_64                        834/1201 
  Verifying        : mozjs60-60.9.0-4.el8.x86_64                       835/1201 
  Verifying        : mozjs60-60.9.0-4.el8.x86_64                       836/1201 
  Verifying        : mpfr-3.1.6-1.el8.x86_64                           837/1201 
  Verifying        : mpfr-3.1.6-1.el8.x86_64                           838/1201 
  Verifying        : mtr-2:0.92-3.el8.x86_64                           839/1201 
  Verifying        : mtr-2:0.92-3.el8.x86_64                           840/1201 
  Verifying        : nano-2.9.8-1.el8.x86_64                           841/1201 
  Verifying        : nano-2.9.8-1.el8.x86_64                           842/1201 
  Verifying        : net-tools-2.0-0.52.20160912git.el8.x86_64         843/1201 
  Verifying        : net-tools-2.0-0.52.20160912git.el8.x86_64         844/1201 
  Verifying        : newt-0.52.20-11.el8.x86_64                        845/1201 
  Verifying        : newt-0.52.20-11.el8.x86_64                        846/1201 
  Verifying        : nftables-1:0.9.3-18.el8.x86_64                    847/1201 
  Verifying        : nftables-1:0.9.3-18.el8.x86_64                    848/1201 
  Verifying        : npth-1.5-4.el8.x86_64                             849/1201 
  Verifying        : npth-1.5-4.el8.x86_64                             850/1201 
  Verifying        : numactl-libs-2.0.12-11.el8.x86_64                 851/1201 
  Verifying        : numactl-libs-2.0.12-11.el8.x86_64                 852/1201 
  Verifying        : openldap-2.4.46-16.el8.x86_64                     853/1201 
  Verifying        : openldap-2.4.46-16.el8.x86_64                     854/1201 
  Verifying        : openssh-8.0p1-6.el8_4.2.x86_64                    855/1201 
  Verifying        : openssh-8.0p1-6.el8_4.2.x86_64                    856/1201 
  Verifying        : openssh-clients-8.0p1-6.el8_4.2.x86_64            857/1201 
  Verifying        : openssh-clients-8.0p1-6.el8_4.2.x86_64            858/1201 
  Verifying        : openssh-server-8.0p1-6.el8_4.2.x86_64             859/1201 
  Verifying        : openssh-server-8.0p1-6.el8_4.2.x86_64             860/1201 
  Verifying        : openssl-1:1.1.1g-15.el8_3.x86_64                  861/1201 
  Verifying        : openssl-1:1.1.1g-15.el8_3.x86_64                  862/1201 
  Verifying        : openssl-libs-1:1.1.1g-15.el8_3.x86_64             863/1201 
  Verifying        : openssl-libs-1:1.1.1g-15.el8_3.x86_64             864/1201 
  Verifying        : openssl-pkcs11-0.4.10-2.el8.x86_64                865/1201 
  Verifying        : openssl-pkcs11-0.4.10-2.el8.x86_64                866/1201 
  Verifying        : os-prober-1.74-6.el8.x86_64                       867/1201 
  Verifying        : os-prober-1.74-6.el8.x86_64                       868/1201 
  Verifying        : p11-kit-0.23.22-1.el8.x86_64                      869/1201 
  Verifying        : p11-kit-0.23.22-1.el8.x86_64                      870/1201 
  Verifying        : p11-kit-trust-0.23.22-1.el8.x86_64                871/1201 
  Verifying        : p11-kit-trust-0.23.22-1.el8.x86_64                872/1201 
  Verifying        : pam-1.3.1-14.el8.x86_64                           873/1201 
  Verifying        : pam-1.3.1-14.el8.x86_64                           874/1201 
  Verifying        : parted-3.2-38.el8.x86_64                          875/1201 
  Verifying        : parted-3.2-38.el8.x86_64                          876/1201 
  Verifying        : passwd-0.80-3.el8.x86_64                          877/1201 
  Verifying        : passwd-0.80-3.el8.x86_64                          878/1201 
  Verifying        : pciutils-3.7.0-1.el8.x86_64                       879/1201 
  Verifying        : pciutils-3.7.0-1.el8.x86_64                       880/1201 
  Verifying        : pciutils-libs-3.7.0-1.el8.x86_64                  881/1201 
  Verifying        : pciutils-libs-3.7.0-1.el8.x86_64                  882/1201 
  Verifying        : pcre-8.42-4.el8.x86_64                            883/1201 
  Verifying        : pcre-8.42-4.el8.x86_64                            884/1201 
  Verifying        : pcre2-10.32-2.el8.x86_64                          885/1201 
  Verifying        : pcre2-10.32-2.el8.x86_64                          886/1201 
  Verifying        : pigz-2.4-4.el8.x86_64                             887/1201 
  Verifying        : pigz-2.4-4.el8.x86_64                             888/1201 
  Verifying        : pkgconf-1.4.2-1.el8.x86_64                        889/1201 
  Verifying        : pkgconf-1.4.2-1.el8.x86_64                        890/1201 
  Verifying        : pkgconf-m4-1.4.2-1.el8.noarch                     891/1201 
  Verifying        : pkgconf-m4-1.4.2-1.el8.noarch                     892/1201 
  Verifying        : pkgconf-pkg-config-1.4.2-1.el8.x86_64             893/1201 
  Verifying        : pkgconf-pkg-config-1.4.2-1.el8.x86_64             894/1201 
  Verifying        : platform-python-setuptools-39.2.0-6.el8.noarch    895/1201 
  Verifying        : platform-python-setuptools-39.2.0-6.el8.noarch    896/1201 
  Verifying        : policycoreutils-2.9-14.el8.x86_64                 897/1201 
  Verifying        : policycoreutils-2.9-14.el8.x86_64                 898/1201 
  Verifying        : policycoreutils-python-utils-2.9-14.el8.noarch    899/1201 
  Verifying        : policycoreutils-python-utils-2.9-14.el8.noarch    900/1201 
  Verifying        : polkit-0.115-11.el8_4.1.x86_64                    901/1201 
  Verifying        : polkit-0.115-11.el8_4.1.x86_64                    902/1201 
  Verifying        : polkit-libs-0.115-11.el8_4.1.x86_64               903/1201 
  Verifying        : polkit-libs-0.115-11.el8_4.1.x86_64               904/1201 
  Verifying        : polkit-pkla-compat-0.1-12.el8.x86_64              905/1201 
  Verifying        : polkit-pkla-compat-0.1-12.el8.x86_64              906/1201 
  Verifying        : popt-1.18-1.el8.x86_64                            907/1201 
  Verifying        : popt-1.18-1.el8.x86_64                            908/1201 
  Verifying        : prefixdevname-0.1.0-6.el8.x86_64                  909/1201 
  Verifying        : prefixdevname-0.1.0-6.el8.x86_64                  910/1201 
  Verifying        : procps-ng-3.3.15-6.el8.x86_64                     911/1201 
  Verifying        : procps-ng-3.3.15-6.el8.x86_64                     912/1201 
  Verifying        : psacct-6.6.3-4.el8.x86_64                         913/1201 
  Verifying        : psacct-6.6.3-4.el8.x86_64                         914/1201 
  Verifying        : psmisc-23.1-5.el8.x86_64                          915/1201 
  Verifying        : psmisc-23.1-5.el8.x86_64                          916/1201 
  Verifying        : publicsuffix-list-dafsa-20180723-1.el8.noarch     917/1201 
  Verifying        : publicsuffix-list-dafsa-20180723-1.el8.noarch     918/1201 
  Verifying        : python3-configobj-5.0.6-11.el8.noarch             919/1201 
  Verifying        : python3-configobj-5.0.6-11.el8.noarch             920/1201 
  Verifying        : python3-dateutil-1:2.6.1-6.el8.noarch             921/1201 
  Verifying        : python3-dateutil-1:2.6.1-6.el8.noarch             922/1201 
  Verifying        : python3-dbus-1.2.4-15.el8.x86_64                  923/1201 
  Verifying        : python3-dbus-1.2.4-15.el8.x86_64                  924/1201 
  Verifying        : python3-decorator-4.2.1-2.el8.noarch              925/1201 
  Verifying        : python3-decorator-4.2.1-2.el8.noarch              926/1201 
  Verifying        : python3-dnf-4.4.2-11.el8.noarch                   927/1201 
  Verifying        : python3-dnf-4.4.2-11.el8.noarch                   928/1201 
  Verifying        : python3-dnf-plugins-core-4.0.18-4.el8.noarch      929/1201 
  Verifying        : python3-dnf-plugins-core-4.0.18-4.el8.noarch      930/1201 
  Verifying        : python3-firewall-0.8.2-6.el8.noarch               931/1201 
  Verifying        : python3-firewall-0.8.2-6.el8.noarch               932/1201 
  Verifying        : python3-gobject-base-3.28.3-2.el8.x86_64          933/1201 
  Verifying        : python3-gobject-base-3.28.3-2.el8.x86_64          934/1201 
  Verifying        : python3-gpg-1.13.1-7.el8.x86_64                   935/1201 
  Verifying        : python3-gpg-1.13.1-7.el8.x86_64                   936/1201 
  Verifying        : python3-hawkey-0.55.0-7.el8.x86_64                937/1201 
  Verifying        : python3-hawkey-0.55.0-7.el8.x86_64                938/1201 
  Verifying        : python3-libcomps-0.1.11-5.el8.x86_64              939/1201 
  Verifying        : python3-libcomps-0.1.11-5.el8.x86_64              940/1201 
  Verifying        : python3-libdnf-0.55.0-7.el8.x86_64                941/1201 
  Verifying        : python3-libdnf-0.55.0-7.el8.x86_64                942/1201 
  Verifying        : python3-libselinux-2.9-5.el8.x86_64               943/1201 
  Verifying        : python3-libselinux-2.9-5.el8.x86_64               944/1201 
  Verifying        : python3-libsemanage-2.9-6.el8.x86_64              945/1201 
  Verifying        : python3-libsemanage-2.9-6.el8.x86_64              946/1201 
  Verifying        : python3-libstoragemgmt-1.8.7-1.el8.noarch         947/1201 
  Verifying        : python3-libstoragemgmt-1.8.7-1.el8.noarch         948/1201 
  Verifying        : python3-libstoragemgmt-clibs-1.8.7-1.el8.x86_6    949/1201 
  Verifying        : python3-libstoragemgmt-clibs-1.8.7-1.el8.x86_6    950/1201 
  Verifying        : python3-libxml2-2.9.7-9.el8.x86_64                951/1201 
  Verifying        : python3-libxml2-2.9.7-9.el8.x86_64                952/1201 
  Verifying        : python3-linux-procfs-0.6.3-1.el8.noarch           953/1201 
  Verifying        : python3-linux-procfs-0.6.3-1.el8.noarch           954/1201 
  Verifying        : python3-nftables-1:0.9.3-18.el8.x86_64            955/1201 
  Verifying        : python3-nftables-1:0.9.3-18.el8.x86_64            956/1201 
  Verifying        : python3-ply-3.9-9.el8.noarch                      957/1201 
  Verifying        : python3-ply-3.9-9.el8.noarch                      958/1201 
  Verifying        : python3-policycoreutils-2.9-14.el8.noarch         959/1201 
  Verifying        : python3-policycoreutils-2.9-14.el8.noarch         960/1201 
  Verifying        : python3-pyudev-0.21.0-7.el8.noarch                961/1201 
  Verifying        : python3-pyudev-0.21.0-7.el8.noarch                962/1201 
  Verifying        : python3-pyyaml-3.12-12.el8.x86_64                 963/1201 
  Verifying        : python3-pyyaml-3.12-12.el8.x86_64                 964/1201 
  Verifying        : python3-rpm-4.14.3-13.el8.x86_64                  965/1201 
  Verifying        : python3-rpm-4.14.3-13.el8.x86_64                  966/1201 
  Verifying        : python3-schedutils-0.6-6.el8.x86_64               967/1201 
  Verifying        : python3-schedutils-0.6-6.el8.x86_64               968/1201 
  Verifying        : python3-setools-4.3.0-2.el8.x86_64                969/1201 
  Verifying        : python3-setools-4.3.0-2.el8.x86_64                970/1201 
  Verifying        : python3-setuptools-39.2.0-6.el8.noarch            971/1201 
  Verifying        : python3-setuptools-39.2.0-6.el8.noarch            972/1201 
  Verifying        : python3-setuptools-wheel-39.2.0-6.el8.noarch      973/1201 
  Verifying        : python3-setuptools-wheel-39.2.0-6.el8.noarch      974/1201 
  Verifying        : python3-six-1.11.0-8.el8.noarch                   975/1201 
  Verifying        : python3-six-1.11.0-8.el8.noarch                   976/1201 
  Verifying        : python3-slip-0.6.4-11.el8.noarch                  977/1201 
  Verifying        : python3-slip-0.6.4-11.el8.noarch                  978/1201 
  Verifying        : python3-slip-dbus-0.6.4-11.el8.noarch             979/1201 
  Verifying        : python3-slip-dbus-0.6.4-11.el8.noarch             980/1201 
  Verifying        : python3-sssdconfig-2.4.0-9.el8.noarch             981/1201 
  Verifying        : python3-sssdconfig-2.4.0-9.el8.noarch             982/1201 
  Verifying        : python3-syspurpose-1.28.13-2.el8.x86_64           983/1201 
  Verifying        : python3-syspurpose-1.28.13-2.el8.x86_64           984/1201 
  Verifying        : quota-1:4.04-12.el8.x86_64                        985/1201 
  Verifying        : quota-1:4.04-12.el8.x86_64                        986/1201 
  Verifying        : quota-nls-1:4.04-12.el8.noarch                    987/1201 
  Verifying        : quota-nls-1:4.04-12.el8.noarch                    988/1201 
  Verifying        : rdma-core-32.0-4.el8.x86_64                       989/1201 
  Verifying        : rdma-core-32.0-4.el8.x86_64                       990/1201 
  Verifying        : readline-7.0-10.el8.x86_64                        991/1201 
  Verifying        : readline-7.0-10.el8.x86_64                        992/1201 
  Verifying        : realmd-0.16.3-22.el8.x86_64                       993/1201 
  Verifying        : realmd-0.16.3-22.el8.x86_64                       994/1201 
  Verifying        : rootfiles-8.1-22.el8.noarch                       995/1201 
  Verifying        : rootfiles-8.1-22.el8.noarch                       996/1201 
  Verifying        : rpm-4.14.3-13.el8.x86_64                          997/1201 
  Verifying        : rpm-4.14.3-13.el8.x86_64                          998/1201 
  Verifying        : rpm-build-libs-4.14.3-13.el8.x86_64               999/1201 
  Verifying        : rpm-build-libs-4.14.3-13.el8.x86_64              1000/1201 
  Verifying        : rpm-libs-4.14.3-13.el8.x86_64                    1001/1201 
  Verifying        : rpm-libs-4.14.3-13.el8.x86_64                    1002/1201 
  Verifying        : rpm-plugin-selinux-4.14.3-13.el8.x86_64          1003/1201 
  Verifying        : rpm-plugin-selinux-4.14.3-13.el8.x86_64          1004/1201 
  Verifying        : rpm-plugin-systemd-inhibit-4.14.3-13.el8.x86_6   1005/1201 
  Verifying        : rpm-plugin-systemd-inhibit-4.14.3-13.el8.x86_6   1006/1201 
  Verifying        : rsync-3.1.3-12.el8.x86_64                        1007/1201 
  Verifying        : rsync-3.1.3-12.el8.x86_64                        1008/1201 
  Verifying        : samba-client-libs-4.13.3-3.el8.x86_64            1009/1201 
  Verifying        : samba-client-libs-4.13.3-3.el8.x86_64            1010/1201 
  Verifying        : samba-common-4.13.3-3.el8.noarch                 1011/1201 
  Verifying        : samba-common-4.13.3-3.el8.noarch                 1012/1201 
  Verifying        : samba-common-libs-4.13.3-3.el8.x86_64            1013/1201 
  Verifying        : samba-common-libs-4.13.3-3.el8.x86_64            1014/1201 
  Verifying        : sed-4.5-2.el8.x86_64                             1015/1201 
  Verifying        : sed-4.5-2.el8.x86_64                             1016/1201 
  Verifying        : selinux-policy-3.14.3-67.el8.noarch              1017/1201 
  Verifying        : selinux-policy-3.14.3-67.el8.noarch              1018/1201 
  Verifying        : selinux-policy-targeted-3.14.3-67.el8.noarch     1019/1201 
  Verifying        : selinux-policy-targeted-3.14.3-67.el8.noarch     1020/1201 
  Verifying        : setup-2.12.2-6.el8.noarch                        1021/1201 
  Verifying        : setup-2.12.2-6.el8.noarch                        1022/1201 
  Verifying        : sg3_utils-1.44-5.el8.x86_64                      1023/1201 
  Verifying        : sg3_utils-1.44-5.el8.x86_64                      1024/1201 
  Verifying        : sg3_utils-libs-1.44-5.el8.x86_64                 1025/1201 
  Verifying        : sg3_utils-libs-1.44-5.el8.x86_64                 1026/1201 
  Verifying        : shadow-utils-2:4.6-12.el8.x86_64                 1027/1201 
  Verifying        : shadow-utils-2:4.6-12.el8.x86_64                 1028/1201 
  Verifying        : shared-mime-info-1.9-3.el8.x86_64                1029/1201 
  Verifying        : shared-mime-info-1.9-3.el8.x86_64                1030/1201 
  Verifying        : slang-2.3.2-3.el8.x86_64                         1031/1201 
  Verifying        : slang-2.3.2-3.el8.x86_64                         1032/1201 
  Verifying        : smartmontools-1:7.1-1.el8.x86_64                 1033/1201 
  Verifying        : smartmontools-1:7.1-1.el8.x86_64                 1034/1201 
  Verifying        : snappy-1.1.8-3.el8.x86_64                        1035/1201 
  Verifying        : snappy-1.1.8-3.el8.x86_64                        1036/1201 
  Verifying        : sos-4.0-11.el8.noarch                            1037/1201 
  Verifying        : sos-4.0-11.el8.noarch                            1038/1201 
  Verifying        : sqlite-3.26.0-13.el8.x86_64                      1039/1201 
  Verifying        : sqlite-3.26.0-13.el8.x86_64                      1040/1201 
  Verifying        : sqlite-libs-3.26.0-13.el8.x86_64                 1041/1201 
  Verifying        : sqlite-libs-3.26.0-13.el8.x86_64                 1042/1201 
  Verifying        : squashfs-tools-4.3-20.el8.x86_64                 1043/1201 
  Verifying        : squashfs-tools-4.3-20.el8.x86_64                 1044/1201 
  Verifying        : sssd-2.4.0-9.el8.x86_64                          1045/1201 
  Verifying        : sssd-2.4.0-9.el8.x86_64                          1046/1201 
  Verifying        : sssd-ad-2.4.0-9.el8.x86_64                       1047/1201 
  Verifying        : sssd-ad-2.4.0-9.el8.x86_64                       1048/1201 
  Verifying        : sssd-client-2.4.0-9.el8.x86_64                   1049/1201 
  Verifying        : sssd-client-2.4.0-9.el8.x86_64                   1050/1201 
  Verifying        : sssd-common-2.4.0-9.el8.x86_64                   1051/1201 
  Verifying        : sssd-common-2.4.0-9.el8.x86_64                   1052/1201 
  Verifying        : sssd-common-pac-2.4.0-9.el8.x86_64               1053/1201 
  Verifying        : sssd-common-pac-2.4.0-9.el8.x86_64               1054/1201 
  Verifying        : sssd-ipa-2.4.0-9.el8.x86_64                      1055/1201 
  Verifying        : sssd-ipa-2.4.0-9.el8.x86_64                      1056/1201 
  Verifying        : sssd-kcm-2.4.0-9.el8.x86_64                      1057/1201 
  Verifying        : sssd-kcm-2.4.0-9.el8.x86_64                      1058/1201 
  Verifying        : sssd-krb5-2.4.0-9.el8.x86_64                     1059/1201 
  Verifying        : sssd-krb5-2.4.0-9.el8.x86_64                     1060/1201 
  Verifying        : sssd-krb5-common-2.4.0-9.el8.x86_64              1061/1201 
  Verifying        : sssd-krb5-common-2.4.0-9.el8.x86_64              1062/1201 
  Verifying        : sssd-ldap-2.4.0-9.el8.x86_64                     1063/1201 
  Verifying        : sssd-ldap-2.4.0-9.el8.x86_64                     1064/1201 
  Verifying        : sssd-nfs-idmap-2.4.0-9.el8.x86_64                1065/1201 
  Verifying        : sssd-nfs-idmap-2.4.0-9.el8.x86_64                1066/1201 
  Verifying        : sssd-proxy-2.4.0-9.el8.x86_64                    1067/1201 
  Verifying        : sssd-proxy-2.4.0-9.el8.x86_64                    1068/1201 
  Verifying        : strace-5.7-2.el8.x86_64                          1069/1201 
  Verifying        : strace-5.7-2.el8.x86_64                          1070/1201 
  Verifying        : sudo-1.8.29-7.el8.x86_64                         1071/1201 
  Verifying        : sudo-1.8.29-7.el8.x86_64                         1072/1201 
  Verifying        : symlinks-1.4-19.el8.x86_64                       1073/1201 
  Verifying        : symlinks-1.4-19.el8.x86_64                       1074/1201 
  Verifying        : systemd-239-45.el8.x86_64                        1075/1201 
  Verifying        : systemd-239-45.el8.x86_64                        1076/1201 
  Verifying        : systemd-libs-239-45.el8.x86_64                   1077/1201 
  Verifying        : systemd-libs-239-45.el8.x86_64                   1078/1201 
  Verifying        : systemd-pam-239-45.el8.x86_64                    1079/1201 
  Verifying        : systemd-pam-239-45.el8.x86_64                    1080/1201 
  Verifying        : systemd-udev-239-45.el8.x86_64                   1081/1201 
  Verifying        : systemd-udev-239-45.el8.x86_64                   1082/1201 
  Verifying        : tar-2:1.30-5.el8.x86_64                          1083/1201 
  Verifying        : tar-2:1.30-5.el8.x86_64                          1084/1201 
  Verifying        : teamd-1.31-2.el8.x86_64                          1085/1201 
  Verifying        : teamd-1.31-2.el8.x86_64                          1086/1201 
  Verifying        : time-1.9-3.el8.x86_64                            1087/1201 
  Verifying        : time-1.9-3.el8.x86_64                            1088/1201 
  Verifying        : timedatex-0.5-3.el8.x86_64                       1089/1201 
  Verifying        : timedatex-0.5-3.el8.x86_64                       1090/1201 
  Verifying        : tpm2-tools-4.1.1-2.el8.x86_64                    1091/1201 
  Verifying        : tpm2-tools-4.1.1-2.el8.x86_64                    1092/1201 
  Verifying        : tpm2-tss-2.3.2-3.el8.x86_64                      1093/1201 
  Verifying        : tpm2-tss-2.3.2-3.el8.x86_64                      1094/1201 
  Verifying        : tree-1.7.0-15.el8.x86_64                         1095/1201 
  Verifying        : tree-1.7.0-15.el8.x86_64                         1096/1201 
  Verifying        : trousers-0.3.15-1.el8.x86_64                     1097/1201 
  Verifying        : trousers-0.3.15-1.el8.x86_64                     1098/1201 
  Verifying        : trousers-lib-0.3.15-1.el8.x86_64                 1099/1201 
  Verifying        : trousers-lib-0.3.15-1.el8.x86_64                 1100/1201 
  Verifying        : tuned-2.15.0-2.el8.noarch                        1101/1201 
  Verifying        : tuned-2.15.0-2.el8.noarch                        1102/1201 
  Verifying        : tzdata-2021a-1.el8.noarch                        1103/1201 
  Verifying        : tzdata-2021a-1.el8.noarch                        1104/1201 
  Verifying        : unzip-6.0-44.el8.x86_64                          1105/1201 
  Verifying        : unzip-6.0-44.el8.x86_64                          1106/1201 
  Verifying        : usb_modeswitch-data-20191128-1.el8.noarch        1107/1201 
  Verifying        : usb_modeswitch-data-20191128-1.el8.noarch        1108/1201 
  Verifying        : usbutils-010-3.el8.x86_64                        1109/1201 
  Verifying        : usbutils-010-3.el8.x86_64                        1110/1201 
  Verifying        : userspace-rcu-0.10.1-4.el8.x86_64                1111/1201 
  Verifying        : userspace-rcu-0.10.1-4.el8.x86_64                1112/1201 
  Verifying        : util-linux-2.32.1-27.el8.x86_64                  1113/1201 
  Verifying        : util-linux-2.32.1-27.el8.x86_64                  1114/1201 
  Verifying        : util-linux-user-2.32.1-27.el8.x86_64             1115/1201 
  Verifying        : util-linux-user-2.32.1-27.el8.x86_64             1116/1201 
  Verifying        : vdo-6.2.4.14-14.el8.x86_64                       1117/1201 
  Verifying        : vdo-6.2.4.14-14.el8.x86_64                       1118/1201 
  Verifying        : vim-minimal-2:8.0.1763-15.el8.x86_64             1119/1201 
  Verifying        : vim-minimal-2:8.0.1763-15.el8.x86_64             1120/1201 
  Verifying        : virt-what-1.18-6.el8.x86_64                      1121/1201 
  Verifying        : virt-what-1.18-6.el8.x86_64                      1122/1201 
  Verifying        : which-2.21-12.el8.x86_64                         1123/1201 
  Verifying        : which-2.21-12.el8.x86_64                         1124/1201 
  Verifying        : words-3.0-28.el8.noarch                          1125/1201 
  Verifying        : words-3.0-28.el8.noarch                          1126/1201 
  Verifying        : xfsdump-3.1.8-2.el8.x86_64                       1127/1201 
  Verifying        : xfsdump-3.1.8-2.el8.x86_64                       1128/1201 
  Verifying        : xfsprogs-5.0.0-8.el8.x86_64                      1129/1201 
  Verifying        : xfsprogs-5.0.0-8.el8.x86_64                      1130/1201 
  Verifying        : yum-4.4.2-11.el8.noarch                          1131/1201 
  Verifying        : yum-4.4.2-11.el8.noarch                          1132/1201 
  Verifying        : zip-3.0-23.el8.x86_64                            1133/1201 
  Verifying        : zip-3.0-23.el8.x86_64                            1134/1201 
  Verifying        : zlib-1.2.11-17.el8.x86_64                        1135/1201 
  Verifying        : zlib-1.2.11-17.el8.x86_64                        1136/1201 
  Verifying        : kernel-4.18.0-305.3.1.el8_4.x86_64               1137/1201 
  Verifying        : kernel-core-4.18.0-305.3.1.el8_4.x86_64          1138/1201 
  Verifying        : kernel-modules-4.18.0-305.3.1.el8_4.x86_64       1139/1201 
  Verifying        : rsyslog-8.1911.0-7.el8.1.x86_64                  1140/1201 
  Verifying        : rsyslog-8.1911.0-7.el8.x86_64                    1141/1201 
  Verifying        : rsyslog-gnutls-8.1911.0-7.el8.1.x86_64           1142/1201 
  Verifying        : rsyslog-gnutls-8.1911.0-7.el8.x86_64             1143/1201 
  Verifying        : rsyslog-gssapi-8.1911.0-7.el8.1.x86_64           1144/1201 
  Verifying        : rsyslog-gssapi-8.1911.0-7.el8.x86_64             1145/1201 
  Verifying        : rsyslog-relp-8.1911.0-7.el8.1.x86_64             1146/1201 
  Verifying        : rsyslog-relp-8.1911.0-7.el8.x86_64               1147/1201 
  Verifying        : acl-2.2.53-1.el8.1.x86_64                        1148/1201 
  Verifying        : acl-2.2.53-1.el8.x86_64                          1149/1201 
  Verifying        : audit-3.0-0.17.20191104git1c2f876.el8.1.x86_64   1150/1201 
  Verifying        : audit-3.0-0.17.20191104git1c2f876.el8.x86_64     1151/1201 
  Verifying        : audit-libs-3.0-0.17.20191104git1c2f876.el8.1.x   1152/1201 
  Verifying        : audit-libs-3.0-0.17.20191104git1c2f876.el8.x86   1153/1201 
  Verifying        : bpftool-4.18.0-305.3.1.el8_4.x86_64              1154/1201 
  Verifying        : bpftool-4.18.0-305.3.1.el8.x86_64                1155/1201 
  Verifying        : e2fsprogs-1.45.6-1.el8.1.x86_64                  1156/1201 
  Verifying        : e2fsprogs-1.45.6-1.el8.x86_64                    1157/1201 
  Verifying        : e2fsprogs-libs-1.45.6-1.el8.1.x86_64             1158/1201 
  Verifying        : e2fsprogs-libs-1.45.6-1.el8.x86_64               1159/1201 
  Verifying        : jimtcl-0.77-6.el8.1.x86_64                       1160/1201 
  Verifying        : jimtcl-0.77-6.el8.x86_64                         1161/1201 
  Verifying        : kernel-tools-4.18.0-305.3.1.el8_4.x86_64         1162/1201 
  Verifying        : kernel-tools-4.18.0-305.3.1.el8.x86_64           1163/1201 
  Verifying        : kernel-tools-libs-4.18.0-305.3.1.el8_4.x86_64    1164/1201 
  Verifying        : kernel-tools-libs-4.18.0-305.3.1.el8.x86_64      1165/1201 
  Verifying        : libacl-2.2.53-1.el8.1.x86_64                     1166/1201 
  Verifying        : libacl-2.2.53-1.el8.x86_64                       1167/1201 
  Verifying        : libcom_err-1.45.6-1.el8.1.x86_64                 1168/1201 
  Verifying        : libcom_err-1.45.6-1.el8.x86_64                   1169/1201 
  Verifying        : libnghttp2-1.33.0-3.el8_3.1.x86_64               1170/1201 
  Verifying        : libnghttp2-1.33.0-3.el8_2.1.x86_64               1171/1201 
  Verifying        : libreport-filesystem-2.9.5-15.el8.rocky.1.x86_   1172/1201 
  Verifying        : libreport-filesystem-2.9.5-15.el8.x86_64         1173/1201 
  Verifying        : libss-1.45.6-1.el8.1.x86_64                      1174/1201 
  Verifying        : libss-1.45.6-1.el8.x86_64                        1175/1201 
  Verifying        : ncurses-6.1-7.20180224.el8.1.x86_64              1176/1201 
  Verifying        : ncurses-6.1-7.20180224.el8.x86_64                1177/1201 
  Verifying        : ncurses-base-6.1-7.20180224.el8.1.noarch         1178/1201 
  Verifying        : ncurses-base-6.1-7.20180224.el8.noarch           1179/1201 
  Verifying        : ncurses-libs-6.1-7.20180224.el8.1.x86_64         1180/1201 
  Verifying        : ncurses-libs-6.1-7.20180224.el8.x86_64           1181/1201 
  Verifying        : nettle-3.4.1-4.el8_4.x86_64                      1182/1201 
  Verifying        : nettle-3.4.1-4.el8_3.x86_64                      1183/1201 
  Verifying        : platform-python-3.6.8-37.el8.rocky.x86_64        1184/1201 
  Verifying        : platform-python-3.6.8-37.el8.x86_64              1185/1201 
  Verifying        : platform-python-pip-9.0.3-19.el8.rocky.noarch    1186/1201 
  Verifying        : platform-python-pip-9.0.3-19.el8.noarch          1187/1201 
  Verifying        : python3-audit-3.0-0.17.20191104git1c2f876.el8.   1188/1201 
  Verifying        : python3-audit-3.0-0.17.20191104git1c2f876.el8.   1189/1201 
  Verifying        : python3-libs-3.6.8-37.el8.rocky.x86_64           1190/1201 
  Verifying        : python3-libs-3.6.8-37.el8.x86_64                 1191/1201 
  Verifying        : python3-perf-4.18.0-305.3.1.el8_4.x86_64         1192/1201 
  Verifying        : python3-perf-4.18.0-305.3.1.el8.x86_64           1193/1201 
  Verifying        : python3-pip-wheel-9.0.3-19.el8.rocky.noarch      1194/1201 
  Verifying        : python3-pip-wheel-9.0.3-19.el8.noarch            1195/1201 
  Verifying        : usb_modeswitch-2.5.2-1.el8.2.x86_64              1196/1201 
  Verifying        : usb_modeswitch-2.5.2-1.el8.x86_64                1197/1201 
  Verifying        : xz-5.2.4-3.el8.1.x86_64                          1198/1201 
  Verifying        : xz-5.2.4-3.el8.x86_64                            1199/1201 
  Verifying        : xz-libs-5.2.4-3.el8.1.x86_64                     1200/1201 
  Verifying        : xz-libs-5.2.4-3.el8.x86_64                       1201/1201 

Upgraded:
  acl-2.2.53-1.el8.1.x86_64                                                     
  audit-3.0-0.17.20191104git1c2f876.el8.1.x86_64                                
  audit-libs-3.0-0.17.20191104git1c2f876.el8.1.x86_64                           
  bpftool-4.18.0-305.3.1.el8_4.x86_64                                           
  e2fsprogs-1.45.6-1.el8.1.x86_64                                               
  e2fsprogs-libs-1.45.6-1.el8.1.x86_64                                          
  jimtcl-0.77-6.el8.1.x86_64                                                    
  kernel-tools-4.18.0-305.3.1.el8_4.x86_64                                      
  kernel-tools-libs-4.18.0-305.3.1.el8_4.x86_64                                 
  libacl-2.2.53-1.el8.1.x86_64                                                  
  libcom_err-1.45.6-1.el8.1.x86_64                                              
  libnghttp2-1.33.0-3.el8_3.1.x86_64                                            
  libreport-filesystem-2.9.5-15.el8.rocky.1.x86_64                              
  libss-1.45.6-1.el8.1.x86_64                                                   
  ncurses-6.1-7.20180224.el8.1.x86_64                                           
  ncurses-base-6.1-7.20180224.el8.1.noarch                                      
  ncurses-libs-6.1-7.20180224.el8.1.x86_64                                      
  nettle-3.4.1-4.el8_4.x86_64                                                   
  platform-python-3.6.8-37.el8.rocky.x86_64                                     
  platform-python-pip-9.0.3-19.el8.rocky.noarch                                 
  python3-audit-3.0-0.17.20191104git1c2f876.el8.1.x86_64                        
  python3-libs-3.6.8-37.el8.rocky.x86_64                                        
  python3-perf-4.18.0-305.3.1.el8_4.x86_64                                      
  python3-pip-wheel-9.0.3-19.el8.rocky.noarch                                   
  rsyslog-8.1911.0-7.el8.1.x86_64                                               
  rsyslog-gnutls-8.1911.0-7.el8.1.x86_64                                        
  rsyslog-gssapi-8.1911.0-7.el8.1.x86_64                                        
  rsyslog-relp-8.1911.0-7.el8.1.x86_64                                          
  usb_modeswitch-2.5.2-1.el8.2.x86_64                                           
  xz-5.2.4-3.el8.1.x86_64                                                       
  xz-libs-5.2.4-3.el8.1.x86_64                                                  
Downgraded:
  buildah-1.19.7-2.module+el8.4.0+556+40122d08.x86_64                           
  cockpit-podman-29-2.module+el8.4.0+556+40122d08.noarch                        
  conmon-2:2.0.26-3.module+el8.4.0+556+40122d08.x86_64                          
  container-selinux-2:2.162.0-1.module+el8.4.0+556+40122d08.noarch              
  containernetworking-plugins-0.9.1-1.module+el8.4.0+556+40122d08.x86_64        
  containers-common-1:1.2.2-10.module+el8.4.0+556+40122d08.x86_64               
  criu-3.15-1.module+el8.4.0+556+40122d08.x86_64                                
  crun-0.18-2.module+el8.4.0+556+40122d08.x86_64                                
  dhcp-client-12:4.3.6-44.el8_4.1.x86_64                                        
  dhcp-common-12:4.3.6-44.el8_4.1.noarch                                        
  dhcp-libs-12:4.3.6-44.el8_4.1.x86_64                                          
  fuse-overlayfs-1.4.0-3.module+el8.4.0+556+40122d08.x86_64                     
  libslirp-4.3.1-1.module+el8.4.0+556+40122d08.x86_64                           
  nvme-cli-1.12-3.el8.x86_64                                                    
  podman-3.0.1-7.module+el8.4.0+556+40122d08.x86_64                             
  podman-catatonit-3.0.1-7.module+el8.4.0+556+40122d08.x86_64                   
  runc-1.0.0-73.rc93.module+el8.4.0+556+40122d08.x86_64                         
  slirp4netns-1.1.8-1.module+el8.4.0+556+40122d08.x86_64                        
Installed:
  kernel-4.18.0-305.3.1.el8_4.x86_64                                            
  kernel-core-4.18.0-305.3.1.el8_4.x86_64                                       
  kernel-modules-4.18.0-305.3.1.el8_4.x86_64                                    
Reinstalled:
  NetworkManager-1:1.30.0-7.el8.x86_64                                          
  NetworkManager-config-server-1:1.30.0-7.el8.noarch                            
  NetworkManager-libnm-1:1.30.0-7.el8.x86_64                                    
  NetworkManager-team-1:1.30.0-7.el8.x86_64                                     
  NetworkManager-tui-1:1.30.0-7.el8.x86_64                                      
  PackageKit-1.1.12-6.el8.x86_64                                                
  PackageKit-glib-1.1.12-6.el8.x86_64                                           
  abattis-cantarell-fonts-0.0.25-6.el8.noarch                                   
  adcli-0.8.2-9.el8.x86_64                                                      
  alsa-sof-firmware-1.6.1-2.el8.noarch                                          
  at-3.1.20-11.el8.x86_64                                                       
  attr-2.4.48-3.el8.x86_64                                                      
  authselect-1.2.2-2.el8.x86_64                                                 
  authselect-compat-1.2.2-2.el8.x86_64                                          
  authselect-libs-1.2.2-2.el8.x86_64                                            
  avahi-libs-0.7-20.el8.x86_64                                                  
  basesystem-11-5.el8.noarch                                                    
  bash-4.4.20-1.el8_4.x86_64                                                    
  bash-completion-1:2.7-5.el8.noarch                                            
  bc-1.07.1-5.el8.x86_64                                                        
  bind-export-libs-32:9.11.26-4.el8_4.x86_64                                    
  bind-libs-32:9.11.26-4.el8_4.x86_64                                           
  bind-libs-lite-32:9.11.26-4.el8_4.x86_64                                      
  bind-license-32:9.11.26-4.el8_4.noarch                                        
  bind-utils-32:9.11.26-4.el8_4.x86_64                                          
  binutils-2.30-93.el8.x86_64                                                   
  biosdevname-0.7.3-2.el8.x86_64                                                
  blktrace-1.2.0-10.el8.x86_64                                                  
  bolt-0.9.1-1.el8.x86_64                                                       
  brotli-1.0.6-3.el8.x86_64                                                     
  bzip2-1.0.6-26.el8.x86_64                                                     
  bzip2-libs-1.0.6-26.el8.x86_64                                                
  c-ares-1.13.0-5.el8.x86_64                                                    
  ca-certificates-2020.2.41-80.0.el8_2.noarch                                   
  cairo-1.15.12-3.el8.x86_64                                                    
  cairo-gobject-1.15.12-3.el8.x86_64                                            
  checkpolicy-2.9-1.el8.x86_64                                                  
  chkconfig-1.13-2.el8.x86_64                                                   
  chrony-3.5-2.el8.x86_64                                                       
  clevis-15-1.el8.x86_64                                                        
  clevis-luks-15-1.el8.x86_64                                                   
  cockpit-238.2-1.el8.x86_64                                                    
  cockpit-bridge-238.2-1.el8.x86_64                                             
  cockpit-packagekit-238.2-1.el8.noarch                                         
  cockpit-storaged-238.2-1.el8.noarch                                           
  cockpit-system-238.2-1.el8.noarch                                             
  cockpit-ws-238.2-1.el8.x86_64                                                 
  coreutils-8.30-8.el8.x86_64                                                   
  coreutils-common-8.30-8.el8.x86_64                                            
  cpio-2.12-10.el8.x86_64                                                       
  cracklib-2.9.6-15.el8.x86_64                                                  
  cracklib-dicts-2.9.6-15.el8.x86_64                                            
  cronie-1.5.2-4.el8.x86_64                                                     
  cronie-anacron-1.5.2-4.el8.x86_64                                             
  crontabs-1.11-17.20190603git.el8.noarch                                       
  crypto-policies-20210209-1.gitbfb6bed.el8_3.noarch                            
  crypto-policies-scripts-20210209-1.gitbfb6bed.el8_3.noarch                    
  cryptsetup-2.3.3-4.el8.x86_64                                                 
  cryptsetup-libs-2.3.3-4.el8.x86_64                                            
  cups-libs-1:2.2.6-38.el8.x86_64                                               
  curl-7.61.1-18.el8.x86_64                                                     
  cyrus-sasl-gssapi-2.1.27-5.el8.x86_64                                         
  cyrus-sasl-lib-2.1.27-5.el8.x86_64                                            
  cyrus-sasl-plain-2.1.27-5.el8.x86_64                                          
  dbus-1:1.12.8-12.el8_4.2.x86_64                                               
  dbus-common-1:1.12.8-12.el8_4.2.noarch                                        
  dbus-daemon-1:1.12.8-12.el8_4.2.x86_64                                        
  dbus-glib-0.110-2.el8.x86_64                                                  
  dbus-libs-1:1.12.8-12.el8_4.2.x86_64                                          
  dbus-tools-1:1.12.8-12.el8_4.2.x86_64                                         
  dejavu-fonts-common-2.35-7.el8.noarch                                         
  dejavu-sans-mono-fonts-2.35-7.el8.noarch                                      
  desktop-file-utils-0.23-8.el8.x86_64                                          
  device-mapper-8:1.02.175-5.el8.x86_64                                         
  device-mapper-event-8:1.02.175-5.el8.x86_64                                   
  device-mapper-event-libs-8:1.02.175-5.el8.x86_64                              
  device-mapper-libs-8:1.02.175-5.el8.x86_64                                    
  device-mapper-multipath-0.8.4-10.el8.x86_64                                   
  device-mapper-multipath-libs-0.8.4-10.el8.x86_64                              
  device-mapper-persistent-data-0.8.5-4.el8.x86_64                              
  diffutils-3.6-6.el8.x86_64                                                    
  dmidecode-1:3.2-8.el8.x86_64                                                  
  dnf-4.4.2-11.el8.noarch                                                       
  dnf-data-4.4.2-11.el8.noarch                                                  
  dnf-plugins-core-4.0.18-4.el8.noarch                                          
  dos2unix-7.4.0-3.el8.x86_64                                                   
  dosfstools-4.1-6.el8.x86_64                                                   
  dracut-049-135.git20210121.el8.x86_64                                         
  dracut-config-rescue-049-135.git20210121.el8.x86_64                           
  dracut-network-049-135.git20210121.el8.x86_64                                 
  dracut-squash-049-135.git20210121.el8.x86_64                                  
  ed-1.14.2-4.el8.x86_64                                                        
  elfutils-debuginfod-client-0.182-3.el8.x86_64                                 
  elfutils-default-yama-scope-0.182-3.el8.noarch                                
  elfutils-libelf-0.182-3.el8.x86_64                                            
  elfutils-libs-0.182-3.el8.x86_64                                              
  emacs-filesystem-1:26.1-5.el8.noarch                                          
  ethtool-2:5.8-5.el8.x86_64                                                    
  expat-2.2.5-4.el8.x86_64                                                      
  file-5.33-16.el8_3.1.x86_64                                                   
  file-libs-5.33-16.el8_3.1.x86_64                                              
  filesystem-3.8-3.el8.x86_64                                                   
  findutils-1:4.6.0-20.el8.x86_64                                               
  firewalld-0.8.2-6.el8.noarch                                                  
  firewalld-filesystem-0.8.2-6.el8.noarch                                       
  fontconfig-2.13.1-3.el8.x86_64                                                
  fontpackages-filesystem-1.44-22.el8.noarch                                    
  fprintd-1.90.9-2.el8.x86_64                                                   
  fprintd-pam-1.90.9-2.el8.x86_64                                               
  freetype-2.9.1-4.el8_3.1.x86_64                                               
  fstrm-0.6.0-3.el8.1.x86_64                                                    
  fuse-common-3.2.1-12.el8.x86_64                                               
  fuse-libs-2.9.7-12.el8.x86_64                                                 
  fuse3-3.2.1-12.el8.x86_64                                                     
  fuse3-libs-3.2.1-12.el8.x86_64                                                
  gawk-4.2.1-2.el8.x86_64                                                       
  gdbm-1:1.18-1.el8.x86_64                                                      
  gdbm-libs-1:1.18-1.el8.x86_64                                                 
  gdisk-1.0.3-6.el8.x86_64                                                      
  gdk-pixbuf2-2.36.12-5.el8.x86_64                                              
  geolite2-city-20180605-1.el8.noarch                                           
  geolite2-country-20180605-1.el8.noarch                                        
  gettext-0.19.8.1-17.el8.x86_64                                                
  gettext-libs-0.19.8.1-17.el8.x86_64                                           
  glib-networking-2.56.1-1.1.el8.x86_64                                         
  glib2-2.56.4-10.el8_4.x86_64                                                  
  glibc-2.28-151.el8.x86_64                                                     
  glibc-common-2.28-151.el8.x86_64                                              
  glibc-langpack-en-2.28-151.el8.x86_64                                         
  gmp-1:6.1.2-10.el8.x86_64                                                     
  gnupg2-2.2.20-2.el8.x86_64                                                    
  gnupg2-smime-2.2.20-2.el8.x86_64                                              
  gnutls-3.6.14-8.el8_3.x86_64                                                  
  gobject-introspection-1.56.1-1.el8.x86_64                                     
  gpgme-1.13.1-7.el8.x86_64                                                     
  gpm-libs-1.20.7-17.el8.x86_64                                                 
  grep-3.1-6.el8.x86_64                                                         
  groff-base-1.22.3-18.el8.x86_64                                               
  grub2-common-1:2.02-99.el8.noarch                                             
  grub2-pc-1:2.02-99.el8.x86_64                                                 
  grub2-pc-modules-1:2.02-99.el8.noarch                                         
  grub2-tools-1:2.02-99.el8.x86_64                                              
  grub2-tools-extra-1:2.02-99.el8.x86_64                                        
  grub2-tools-minimal-1:2.02-99.el8.x86_64                                      
  grubby-8.40-41.el8.x86_64                                                     
  gsettings-desktop-schemas-3.32.0-5.el8.x86_64                                 
  gzip-1.9-12.el8.x86_64                                                        
  hardlink-1:1.3-6.el8.x86_64                                                   
  hdparm-9.54-3.el8.x86_64                                                      
  hostname-3.20-6.el8.x86_64                                                    
  hwdata-0.314-8.8.el8.noarch                                                   
  ima-evm-utils-1.3.2-12.el8.x86_64                                             
  info-6.5-6.el8.x86_64                                                         
  initscripts-10.00.15-1.el8.x86_64                                             
  ipcalc-0.2.4-4.el8.x86_64                                                     
  iproute-5.9.0-4.el8.x86_64                                                    
  iprutils-2.4.19-1.el8.x86_64                                                  
  ipset-7.1-1.el8.x86_64                                                        
  ipset-libs-7.1-1.el8.x86_64                                                   
  iptables-1.8.4-17.el8.x86_64                                                  
  iptables-ebtables-1.8.4-17.el8.x86_64                                         
  iptables-libs-1.8.4-17.el8.x86_64                                             
  iptstate-2.2.6-6.el8.x86_64                                                   
  iputils-20180629-7.el8.x86_64                                                 
  irqbalance-2:1.4.0-6.el8.x86_64                                               
  iscsi-initiator-utils-6.2.1.2-1.gita8fcb37.el8.x86_64                         
  iscsi-initiator-utils-iscsiuio-6.2.1.2-1.gita8fcb37.el8.x86_64                
  isns-utils-libs-0.99-1.el8.x86_64                                             
  iwl100-firmware-39.31.5.1-102.el8.1.noarch                                    
  iwl1000-firmware-1:39.31.5.1-102.el8.1.noarch                                 
  iwl105-firmware-18.168.6.1-102.el8.1.noarch                                   
  iwl135-firmware-18.168.6.1-102.el8.1.noarch                                   
  iwl2000-firmware-18.168.6.1-102.el8.1.noarch                                  
  iwl2030-firmware-18.168.6.1-102.el8.1.noarch                                  
  iwl3160-firmware-1:25.30.13.0-102.el8.1.noarch                                
  iwl5000-firmware-8.83.5.1_1-102.el8.1.noarch                                  
  iwl5150-firmware-8.24.2.2-102.el8.1.noarch                                    
  iwl6000-firmware-9.221.4.1-102.el8.1.noarch                                   
  iwl6000g2a-firmware-18.168.6.1-102.el8.1.noarch                               
  iwl6000g2b-firmware-18.168.6.1-102.el8.1.noarch                               
  iwl6050-firmware-41.28.5.1-102.el8.1.noarch                                   
  iwl7260-firmware-1:25.30.13.0-102.el8.1.noarch                                
  jansson-2.11-3.el8.x86_64                                                     
  jose-10-2.el8.x86_64                                                          
  jq-1.5-12.el8.x86_64                                                          
  json-c-0.13.1-0.4.el8.x86_64                                                  
  json-glib-1.4.4-1.el8.x86_64                                                  
  kbd-2.0.4-10.el8.x86_64                                                       
  kbd-legacy-2.0.4-10.el8.noarch                                                
  kbd-misc-2.0.4-10.el8.noarch                                                  
  kexec-tools-2.0.20-46.el8.x86_64                                              
  keyutils-libs-1.5.10-6.el8.x86_64                                             
  kmod-25-17.el8.x86_64                                                         
  kmod-kvdo-6.2.4.26-77.el8.x86_64                                              
  kmod-libs-25-17.el8.x86_64                                                    
  kpartx-0.8.4-10.el8.x86_64                                                    
  kpatch-0.9.2-3.el8.noarch                                                     
  kpatch-dnf-0.2-3.el8.noarch                                                   
  krb5-libs-1.18.2-8.el8.x86_64                                                 
  langpacks-en-1.0-12.el8.noarch                                                
  ledmon-0.95-1.el8.x86_64                                                      
  less-530-1.el8.x86_64                                                         
  libX11-1.6.8-4.el8.x86_64                                                     
  libX11-common-1.6.8-4.el8.noarch                                              
  libXau-1.0.9-3.el8.x86_64                                                     
  libXext-1.3.4-1.el8.x86_64                                                    
  libXrender-0.9.10-7.el8.x86_64                                                
  libaio-0.3.112-1.el8.x86_64                                                   
  libappstream-glib-0.7.14-3.el8.x86_64                                         
  libarchive-3.3.3-1.el8.x86_64                                                 
  libassuan-2.5.1-3.el8.x86_64                                                  
  libatasmart-0.19-14.el8.x86_64                                                
  libattr-2.4.48-3.el8.x86_64                                                   
  libbasicobjects-0.1.1-39.el8.x86_64                                           
  libblkid-2.32.1-27.el8.x86_64                                                 
  libblockdev-2.24-5.el8.x86_64                                                 
  libblockdev-crypto-2.24-5.el8.x86_64                                          
  libblockdev-fs-2.24-5.el8.x86_64                                              
  libblockdev-loop-2.24-5.el8.x86_64                                            
  libblockdev-lvm-2.24-5.el8.x86_64                                             
  libblockdev-mdraid-2.24-5.el8.x86_64                                          
  libblockdev-part-2.24-5.el8.x86_64                                            
  libblockdev-swap-2.24-5.el8.x86_64                                            
  libblockdev-utils-2.24-5.el8.x86_64                                           
  libbytesize-1.4-3.el8.x86_64                                                  
  libcap-2.26-4.el8.x86_64                                                      
  libcap-ng-0.7.9-5.el8.x86_64                                                  
  libcollection-0.7.0-39.el8.x86_64                                             
  libcomps-0.1.11-5.el8.x86_64                                                  
  libconfig-1.5-9.el8.x86_64                                                    
  libcroco-0.6.12-4.el8_2.1.x86_64                                              
  libcurl-7.61.1-18.el8.x86_64                                                  
  libdaemon-0.14-15.el8.x86_64                                                  
  libdb-5.3.28-40.el8.x86_64                                                    
  libdb-utils-5.3.28-40.el8.x86_64                                              
  libdhash-0.5.0-39.el8.x86_64                                                  
  libdnf-0.55.0-7.el8.x86_64                                                    
  libedit-3.1-23.20170329cvs.el8.x86_64                                         
  libertas-usb8388-firmware-2:20201218-102.git05789708.el8.noarch               
  libestr-0.1.10-1.el8.x86_64                                                   
  libevent-2.1.8-5.el8.x86_64                                                   
  libfastjson-0.99.8-2.el8.x86_64                                               
  libfdisk-2.32.1-27.el8.x86_64                                                 
  libffi-3.1-22.el8.x86_64                                                      
  libfprint-1.90.7-1.el8.x86_64                                                 
  libgcc-8.4.1-1.el8.x86_64                                                     
  libgcrypt-1.8.5-4.el8.x86_64                                                  
  libgomp-8.4.1-1.el8.x86_64                                                    
  libgpg-error-1.31-1.el8.x86_64                                                
  libgudev-232-4.el8.x86_64                                                     
  libgusb-0.3.0-1.el8.x86_64                                                    
  libibverbs-32.0-4.el8.x86_64                                                  
  libicu-60.3-2.el8_1.x86_64                                                    
  libidn2-2.2.0-1.el8.x86_64                                                    
  libini_config-1.3.1-39.el8.x86_64                                             
  libipa_hbac-2.4.0-9.el8.x86_64                                                
  libjose-10-2.el8.x86_64                                                       
  libkcapi-1.2.0-2.el8.x86_64                                                   
  libkcapi-hmaccalc-1.2.0-2.el8.x86_64                                          
  libksba-1.3.5-7.el8.x86_64                                                    
  libldb-2.2.0-2.el8.x86_64                                                     
  libluksmeta-9-4.el8.x86_64                                                    
  libmaxminddb-1.2.0-10.el8.x86_64                                              
  libmetalink-0.1.3-7.el8.x86_64                                                
  libmnl-1.0.4-6.el8.x86_64                                                     
  libmodman-2.0.1-17.el8.x86_64                                                 
  libmodulemd-2.9.4-2.el8.x86_64                                                
  libmount-2.32.1-27.el8.x86_64                                                 
  libndp-1.7-5.el8.x86_64                                                       
  libnet-1.1.6-15.el8.x86_64                                                    
  libnetfilter_conntrack-1.0.6-5.el8.x86_64                                     
  libnfnetlink-1.0.1-13.el8.x86_64                                              
  libnfsidmap-1:2.3.3-41.el8.x86_64                                             
  libnftnl-1.1.5-4.el8.x86_64                                                   
  libnl3-3.5.0-1.el8.x86_64                                                     
  libnl3-cli-3.5.0-1.el8.x86_64                                                 
  libnsl2-1.2.0-2.20180605git4a062cf.el8.x86_64                                 
  libpath_utils-0.2.1-39.el8.x86_64                                             
  libpcap-14:1.9.1-5.el8.x86_64                                                 
  libpipeline-1.5.0-2.el8.x86_64                                                
  libpkgconf-1.4.2-1.el8.x86_64                                                 
  libpng-2:1.6.34-5.el8.x86_64                                                  
  libproxy-0.4.15-5.2.el8.x86_64                                                
  libpsl-0.20.2-6.el8.x86_64                                                    
  libpwquality-1.4.4-3.el8.x86_64                                               
  libref_array-0.1.5-39.el8.x86_64                                              
  librelp-1.2.16-1.el8.x86_64                                                   
  librepo-1.12.0-3.el8.x86_64                                                   
  libseccomp-2.5.1-1.el8.x86_64                                                 
  libsecret-0.18.6-1.el8.x86_64                                                 
  libselinux-2.9-5.el8.x86_64                                                   
  libselinux-utils-2.9-5.el8.x86_64                                             
  libsemanage-2.9-6.el8.x86_64                                                  
  libsepol-2.9-2.el8.x86_64                                                     
  libsigsegv-2.11-5.el8.x86_64                                                  
  libsmartcols-2.32.1-27.el8.x86_64                                             
  libsmbclient-4.13.3-3.el8.x86_64                                              
  libsolv-0.7.16-2.el8.x86_64                                                   
  libsoup-2.62.3-2.el8.x86_64                                                   
  libssh-0.9.4-2.el8.x86_64                                                     
  libssh-config-0.9.4-2.el8.noarch                                              
  libsss_autofs-2.4.0-9.el8.x86_64                                              
  libsss_certmap-2.4.0-9.el8.x86_64                                             
  libsss_idmap-2.4.0-9.el8.x86_64                                               
  libsss_nss_idmap-2.4.0-9.el8.x86_64                                           
  libsss_sudo-2.4.0-9.el8.x86_64                                                
  libstdc++-8.4.1-1.el8.x86_64                                                  
  libstemmer-0-10.585svn.el8.x86_64                                             
  libstoragemgmt-1.8.7-1.el8.x86_64                                             
  libsysfs-2.1.0-24.el8.x86_64                                                  
  libtalloc-2.3.1-2.el8.x86_64                                                  
  libtasn1-4.13-3.el8.x86_64                                                    
  libtdb-1.4.3-1.el8.x86_64                                                     
  libteam-1.31-2.el8.x86_64                                                     
  libtevent-0.10.2-2.el8.x86_64                                                 
  libtirpc-1.1.4-4.el8.x86_64                                                   
  libudisks2-2.9.0-6.el8.x86_64                                                 
  libunistring-0.9.9-3.el8.x86_64                                               
  libusbx-1.0.23-4.el8.x86_64                                                   
  libuser-0.62-23.el8.x86_64                                                    
  libutempter-1.1.6-14.el8.x86_64                                               
  libuuid-2.32.1-27.el8.x86_64                                                  
  libverto-0.3.0-5.el8.x86_64                                                   
  libwbclient-4.13.3-3.el8.x86_64                                               
  libxcb-1.13.1-1.el8.x86_64                                                    
  libxcrypt-4.1.1-4.el8.x86_64                                                  
  libxkbcommon-0.9.1-1.el8.x86_64                                               
  libxml2-2.9.7-9.el8.x86_64                                                    
  libxslt-1.1.32-6.el8.x86_64                                                   
  libyaml-0.1.7-5.el8.x86_64                                                    
  libzstd-1.4.4-1.el8.x86_64                                                    
  linux-firmware-20201218-102.git05789708.el8.noarch                            
  lmdb-libs-0.9.24-1.el8.x86_64                                                 
  logrotate-3.14.0-4.el8.x86_64                                                 
  lshw-B.02.19.2-5.el8.x86_64                                                   
  lsof-4.93.2-1.el8.x86_64                                                      
  lsscsi-0.32-2.el8.x86_64                                                      
  lua-libs-5.3.4-11.el8.x86_64                                                  
  luksmeta-9-4.el8.x86_64                                                       
  lvm2-8:2.03.11-5.el8.x86_64                                                   
  lvm2-libs-8:2.03.11-5.el8.x86_64                                              
  lz4-libs-1.8.3-2.el8.x86_64                                                   
  lzo-2.08-14.el8.x86_64                                                        
  mailcap-2.1.48-3.el8.noarch                                                   
  man-db-2.7.6.1-17.el8.x86_64                                                  
  man-pages-4.15-6.el8.x86_64                                                   
  man-pages-overrides-8.3.0.2-2.el8.noarch                                      
  mcelog-3:173-0.el8.x86_64                                                     
  mdadm-4.1-15.el8.x86_64                                                       
  memstrack-0.1.11-1.el8.x86_64                                                 
  microcode_ctl-4:20210216-1.20210525.1.el8_4.x86_64                            
  mlocate-0.26-20.el8.x86_64                                                    
  mozjs60-60.9.0-4.el8.x86_64                                                   
  mpfr-3.1.6-1.el8.x86_64                                                       
  mtr-2:0.92-3.el8.x86_64                                                       
  nano-2.9.8-1.el8.x86_64                                                       
  net-tools-2.0-0.52.20160912git.el8.x86_64                                     
  newt-0.52.20-11.el8.x86_64                                                    
  nftables-1:0.9.3-18.el8.x86_64                                                
  nmap-ncat-2:7.70-5.el8.x86_64                                                 
  npth-1.5-4.el8.x86_64                                                         
  nspr-4.25.0-2.el8_2.x86_64                                                    
  nss-3.53.1-17.el8_3.x86_64                                                    
  nss-softokn-3.53.1-17.el8_3.x86_64                                            
  nss-softokn-freebl-3.53.1-17.el8_3.x86_64                                     
  nss-sysinit-3.53.1-17.el8_3.x86_64                                            
  nss-util-3.53.1-17.el8_3.x86_64                                               
  numactl-libs-2.0.12-11.el8.x86_64                                             
  oddjob-0.34.7-1.el8.x86_64                                                    
  oddjob-mkhomedir-0.34.7-1.el8.x86_64                                          
  oniguruma-6.8.2-2.el8.x86_64                                                  
  openldap-2.4.46-16.el8.x86_64                                                 
  openssh-8.0p1-6.el8_4.2.x86_64                                                
  openssh-clients-8.0p1-6.el8_4.2.x86_64                                        
  openssh-server-8.0p1-6.el8_4.2.x86_64                                         
  openssl-1:1.1.1g-15.el8_3.x86_64                                              
  openssl-libs-1:1.1.1g-15.el8_3.x86_64                                         
  openssl-pkcs11-0.4.10-2.el8.x86_64                                            
  os-prober-1.74-6.el8.x86_64                                                   
  p11-kit-0.23.22-1.el8.x86_64                                                  
  p11-kit-trust-0.23.22-1.el8.x86_64                                            
  pam-1.3.1-14.el8.x86_64                                                       
  parted-3.2-38.el8.x86_64                                                      
  passwd-0.80-3.el8.x86_64                                                      
  pciutils-3.7.0-1.el8.x86_64                                                   
  pciutils-libs-3.7.0-1.el8.x86_64                                              
  pcre-8.42-4.el8.x86_64                                                        
  pcre2-10.32-2.el8.x86_64                                                      
  pigz-2.4-4.el8.x86_64                                                         
  pinentry-1.1.0-2.el8.x86_64                                                   
  pinfo-0.6.10-18.el8.x86_64                                                    
  pixman-0.38.4-1.el8.x86_64                                                    
  pkgconf-1.4.2-1.el8.x86_64                                                    
  pkgconf-m4-1.4.2-1.el8.noarch                                                 
  pkgconf-pkg-config-1.4.2-1.el8.x86_64                                         
  platform-python-setuptools-39.2.0-6.el8.noarch                                
  plymouth-0.9.4-9.20200615git1e36e30.el8.x86_64                                
  plymouth-core-libs-0.9.4-9.20200615git1e36e30.el8.x86_64                      
  plymouth-scripts-0.9.4-9.20200615git1e36e30.el8.x86_64                        
  policycoreutils-2.9-14.el8.x86_64                                             
  policycoreutils-python-utils-2.9-14.el8.noarch                                
  polkit-0.115-11.el8_4.1.x86_64                                                
  polkit-libs-0.115-11.el8_4.1.x86_64                                           
  polkit-pkla-compat-0.1-12.el8.x86_64                                          
  popt-1.18-1.el8.x86_64                                                        
  prefixdevname-0.1.0-6.el8.x86_64                                              
  procps-ng-3.3.15-6.el8.x86_64                                                 
  protobuf-c-1.3.0-6.el8.x86_64                                                 
  psacct-6.6.3-4.el8.x86_64                                                     
  psmisc-23.1-5.el8.x86_64                                                      
  publicsuffix-list-dafsa-20180723-1.el8.noarch                                 
  python3-bind-32:9.11.26-4.el8_4.noarch                                        
  python3-cairo-1.16.3-6.el8.x86_64                                             
  python3-configobj-5.0.6-11.el8.noarch                                         
  python3-dateutil-1:2.6.1-6.el8.noarch                                         
  python3-dbus-1.2.4-15.el8.x86_64                                              
  python3-decorator-4.2.1-2.el8.noarch                                          
  python3-dnf-4.4.2-11.el8.noarch                                               
  python3-dnf-plugins-core-4.0.18-4.el8.noarch                                  
  python3-firewall-0.8.2-6.el8.noarch                                           
  python3-gobject-3.28.3-2.el8.x86_64                                           
  python3-gobject-base-3.28.3-2.el8.x86_64                                      
  python3-gpg-1.13.1-7.el8.x86_64                                               
  python3-hawkey-0.55.0-7.el8.x86_64                                            
  python3-html5lib-1:0.999999999-6.el8.noarch                                   
  python3-libcomps-0.1.11-5.el8.x86_64                                          
  python3-libdnf-0.55.0-7.el8.x86_64                                            
  python3-libselinux-2.9-5.el8.x86_64                                           
  python3-libsemanage-2.9-6.el8.x86_64                                          
  python3-libstoragemgmt-1.8.7-1.el8.noarch                                     
  python3-libstoragemgmt-clibs-1.8.7-1.el8.x86_64                               
  python3-libxml2-2.9.7-9.el8.x86_64                                            
  python3-linux-procfs-0.6.3-1.el8.noarch                                       
  python3-lxml-4.2.3-2.el8.x86_64                                               
  python3-nftables-1:0.9.3-18.el8.x86_64                                        
  python3-pexpect-4.3.1-3.el8.noarch                                            
  python3-ply-3.9-9.el8.noarch                                                  
  python3-policycoreutils-2.9-14.el8.noarch                                     
  python3-psutil-5.4.3-10.el8.x86_64                                            
  python3-ptyprocess-0.5.2-4.el8.noarch                                         
  python3-pydbus-0.6.0-5.el8.noarch                                             
  python3-pyudev-0.21.0-7.el8.noarch                                            
  python3-pyyaml-3.12-12.el8.x86_64                                             
  python3-rpm-4.14.3-13.el8.x86_64                                              
  python3-schedutils-0.6-6.el8.x86_64                                           
  python3-setools-4.3.0-2.el8.x86_64                                            
  python3-setuptools-39.2.0-6.el8.noarch                                        
  python3-setuptools-wheel-39.2.0-6.el8.noarch                                  
  python3-six-1.11.0-8.el8.noarch                                               
  python3-slip-0.6.4-11.el8.noarch                                              
  python3-slip-dbus-0.6.4-11.el8.noarch                                         
  python3-sssdconfig-2.4.0-9.el8.noarch                                         
  python3-syspurpose-1.28.13-2.el8.x86_64                                       
  python3-systemd-234-8.el8.x86_64                                              
  python3-tracer-0.7.5-2.el8.noarch                                             
  python3-unbound-1.7.3-15.el8.x86_64                                           
  python3-webencodings-0.5.1-6.el8.noarch                                       
  quota-1:4.04-12.el8.x86_64                                                    
  quota-nls-1:4.04-12.el8.noarch                                                
  rdma-core-32.0-4.el8.x86_64                                                   
  readline-7.0-10.el8.x86_64                                                    
  realmd-0.16.3-22.el8.x86_64                                                   
  rootfiles-8.1-22.el8.noarch                                                   
  rpm-4.14.3-13.el8.x86_64                                                      
  rpm-build-libs-4.14.3-13.el8.x86_64                                           
  rpm-libs-4.14.3-13.el8.x86_64                                                 
  rpm-plugin-selinux-4.14.3-13.el8.x86_64                                       
  rpm-plugin-systemd-inhibit-4.14.3-13.el8.x86_64                               
  rsync-3.1.3-12.el8.x86_64                                                     
  samba-client-libs-4.13.3-3.el8.x86_64                                         
  samba-common-4.13.3-3.el8.noarch                                              
  samba-common-libs-4.13.3-3.el8.x86_64                                         
  sed-4.5-2.el8.x86_64                                                          
  selinux-policy-3.14.3-67.el8.noarch                                           
  selinux-policy-targeted-3.14.3-67.el8.noarch                                  
  setroubleshoot-plugins-3.3.13-1.el8.noarch                                    
  setroubleshoot-server-3.3.24-3.el8.x86_64                                     
  setup-2.12.2-6.el8.noarch                                                     
  sg3_utils-1.44-5.el8.x86_64                                                   
  sg3_utils-libs-1.44-5.el8.x86_64                                              
  shadow-utils-2:4.6-12.el8.x86_64                                              
  shared-mime-info-1.9-3.el8.x86_64                                             
  slang-2.3.2-3.el8.x86_64                                                      
  smartmontools-1:7.1-1.el8.x86_64                                              
  snappy-1.1.8-3.el8.x86_64                                                     
  sos-4.0-11.el8.noarch                                                         
  sqlite-3.26.0-13.el8.x86_64                                                   
  sqlite-libs-3.26.0-13.el8.x86_64                                              
  squashfs-tools-4.3-20.el8.x86_64                                              
  sscg-2.3.3-14.el8.x86_64                                                      
  sssd-2.4.0-9.el8.x86_64                                                       
  sssd-ad-2.4.0-9.el8.x86_64                                                    
  sssd-client-2.4.0-9.el8.x86_64                                                
  sssd-common-2.4.0-9.el8.x86_64                                                
  sssd-common-pac-2.4.0-9.el8.x86_64                                            
  sssd-ipa-2.4.0-9.el8.x86_64                                                   
  sssd-kcm-2.4.0-9.el8.x86_64                                                   
  sssd-krb5-2.4.0-9.el8.x86_64                                                  
  sssd-krb5-common-2.4.0-9.el8.x86_64                                           
  sssd-ldap-2.4.0-9.el8.x86_64                                                  
  sssd-nfs-idmap-2.4.0-9.el8.x86_64                                             
  sssd-proxy-2.4.0-9.el8.x86_64                                                 
  strace-5.7-2.el8.x86_64                                                       
  sudo-1.8.29-7.el8.x86_64                                                      
  symlinks-1.4-19.el8.x86_64                                                    
  systemd-239-45.el8.x86_64                                                     
  systemd-libs-239-45.el8.x86_64                                                
  systemd-pam-239-45.el8.x86_64                                                 
  systemd-udev-239-45.el8.x86_64                                                
  tar-2:1.30-5.el8.x86_64                                                       
  tcpdump-14:4.9.3-1.el8.x86_64                                                 
  teamd-1.31-2.el8.x86_64                                                       
  time-1.9-3.el8.x86_64                                                         
  timedatex-0.5-3.el8.x86_64                                                    
  tpm2-tools-4.1.1-2.el8.x86_64                                                 
  tpm2-tss-2.3.2-3.el8.x86_64                                                   
  tracer-common-0.7.5-2.el8.noarch                                              
  tree-1.7.0-15.el8.x86_64                                                      
  trousers-0.3.15-1.el8.x86_64                                                  
  trousers-lib-0.3.15-1.el8.x86_64                                              
  tuned-2.15.0-2.el8.noarch                                                     
  tzdata-2021a-1.el8.noarch                                                     
  udisks2-2.9.0-6.el8.x86_64                                                    
  udisks2-iscsi-2.9.0-6.el8.x86_64                                              
  udisks2-lvm2-2.9.0-6.el8.x86_64                                               
  unbound-libs-1.7.3-15.el8.x86_64                                              
  unzip-6.0-44.el8.x86_64                                                       
  usb_modeswitch-data-20191128-1.el8.noarch                                     
  usbutils-010-3.el8.x86_64                                                     
  userspace-rcu-0.10.1-4.el8.x86_64                                             
  util-linux-2.32.1-27.el8.x86_64                                               
  util-linux-user-2.32.1-27.el8.x86_64                                          
  vdo-6.2.4.14-14.el8.x86_64                                                    
  vim-common-2:8.0.1763-15.el8.x86_64                                           
  vim-enhanced-2:8.0.1763-15.el8.x86_64                                         
  vim-filesystem-2:8.0.1763-15.el8.noarch                                       
  vim-minimal-2:8.0.1763-15.el8.x86_64                                          
  virt-what-1.18-6.el8.x86_64                                                   
  volume_key-libs-0.3.11-5.el8.x86_64                                           
  wget-1.19.5-10.el8.x86_64                                                     
  which-2.21-12.el8.x86_64                                                      
  words-3.0-28.el8.noarch                                                       
  xdg-utils-1.1.2-5.el8.noarch                                                  
  xfsdump-3.1.8-2.el8.x86_64                                                    
  xfsprogs-5.0.0-8.el8.x86_64                                                   
  xkeyboard-config-2.28-1.el8.noarch                                            
  yajl-2.1.0-10.el8.x86_64                                                      
  yum-4.4.2-11.el8.noarch                                                       
  zip-3.0-23.el8.x86_64                                                         
  zlib-1.2.11-17.el8.x86_64                                                     

Complete!

Done, please reboot your system.
A log of this installation can be found at /var/log/migrate2rocky.log
```
# 3. Update
```
sudo dnf distro-sync -y 
```
4. Reboot
```
sudo reboot
```
5. Cek
```
cat /etc/os-release
```
```
cat /etc/redhat-release
```
# Sumber

[https://ostechnix.com/how-to-migrate-to-rocky-linux-8-from-centos-8-linux/](https://ostechnix.com/how-to-migrate-to-rocky-linux-8-from-centos-8-linux/)

[https://github.com/rocky-linux/rocky-tools/tree/main/migrate2rocky](https://github.com/rocky-linux/rocky-tools/tree/main/migrate2rocky)