Misal saya punya kernel lama

```
5.3.18-59.10.1.x86_64
```

# Masuk sebagai super user (root)

```
su
```

# Lihat daftar kernel yang ada

```
rpm -qa | grep -i kernel-default
```

Hasil:

```
kernel-default-5.3.18-59.13.1.x86_64
kernel-default-optional-5.3.18-59.13.1.x86_64
kernel-default-devel-5.3.18-59.13.1.x86_64
kernel-default-5.3.18-59.10.1.x86_64
kernel-default-optional-5.3.18-59.10.1.x86_64
kernel-default-extra-5.3.18-59.13.1.x86_64
kernel-default-devel-5.3.18-59.10.1.x86_64
kernel-default-extra-5.3.18-59.10.1.x86_64
```

# Cara menghapus

```
rpm -e kernel-default-optional-5.3.18-59.10.1.x86_64
rpm -e kernel-default-extra-5.3.18-59.10.1.x86_64
rpm -e kernel-default-devel-5.3.18-59.10.1.x86_64
rpm -e kernel-default-5.3.18-59.10.1.x86_64
```

# Sumber
[https://gist.github.com/darksystem23/8aef08073b6d6dae705b](https://gist.github.com/darksystem23/8aef08073b6d6dae705b)

