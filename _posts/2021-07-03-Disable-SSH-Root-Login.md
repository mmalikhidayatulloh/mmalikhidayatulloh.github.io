---
layout: post
---
* toc
{:toc}

Untuk meningkatkan keamanan dalam menggunakan ssh maka kita perlu mengatur agar tidak diperbolehkan komputer kita di ssh dan login menggunakan root.

Caranya:
# 1. Edit file /etc/ssh/sshd_config
```
# vim /etc/ssh/sshd_config
```
# 2. Edit
ganti `PermitRootLogin yes`

menjadi
```
PermitRootLogin no
```
# 3. Restart ssh
```
# systemctl restart sshd
```
