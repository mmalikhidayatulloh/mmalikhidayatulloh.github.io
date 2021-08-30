# Cek layar yang dipake

```
xrandr -q | grep ' connected' | head -n 1 | cut -d ' ' -f1
```

di notebook saya outputnya seperti ini:

```
eDP-1
```

# Set kecerahan

Pada contoh ini saya set kecerahan 70%

```
xrandr --output eDP-1 --brightness 0.7
```


# Sumber

[https://unix.stackexchange.com/questions/526653/control-screen-brightness-in-i3](https://unix.stackexchange.com/questions/526653/control-screen-brightness-in-i3)