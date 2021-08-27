DNS (domain name system) used to change ip address which form is number become name with domain. with this method, suppose computer or server with IP address 192.168.43.205 recognize by `malik.net.id`

# Install Pattern DNS Server

***Open YaST*** and choose ***Software > Software Management***. Then choose ***View Patterns*** and choose ***DHCP and DNS Server***. Confirm installation by anwer `ok` to install package with dependency. Or run this command in terminal

```
$ sudo zypper in -t pattern dhcp_dns_server
```

# Configuration

In this case, I set my computer hostname at 

```
# vim /etc/hostname
```

become

```
malik.net.id
```

My ip address is
```
192.168.43.205
```

You can check your ip address by yourself with

```
ifconfig
```

Suppose i will make
```
malik.net.id
lib.malik.net.id
mail.malik.net.id
ns.malik.net.id
www.malik.net.id
```

* First, check `resolv.conf` and `default gateway`

    ```
    # vim /etc/resolv.conf
    ```

    Result

    ```
    search malik.net.id
    nameserver 127.0.0.1
    nameserver 2404:c0:7410:6a2e::1a
    nameserver 192.168.43.1
    ```

    So, i have IPv4 and IPv6

    Then, check default gateway

    ```
    # route
    ```

    Result

    ```
    Kernel IP routing table
    Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
    default         192.168.43.1    0.0.0.0         UG    600    0        0 wlan0
    192.168.43.0    0.0.0.0         255.255.255.0   U     600    0        0 wlan0

    ```

    So, my default gateway is `192.168.43.1`
* Open YaST DNS Server

    ![](/assets/IMG/DNS1.png)

    just hit `Continue`

* Go to `Forwarder` and input your `default gateway` then click `Add`

    ![](/assets/IMG/DNS2.png)

* Go to `Basics Options`

    Set like this

    ```
    allow-query { 127.0.0.1; 192.168.43.1;};
    directory "/var/lib/named";
    disable-empty-zone "1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA";
    dump-file "/var/log/named_dump.db";
    forwarders { 192.168.43.1; };
    include "/etc/named.d/forwarders.conf";
    listen-on port 53 { 127.0.0.1; 192.168.43.1;};
    listen-on-v6 { 2404:c0:7410:6a2e::1a; };
    managed-keys-directory "/var/lib/named/dyn/";
    notify no;
    statistics-file "/var/log/named.stats";
    ```

    ![](/assets/IMG/DNS3.png)

* Go to `DNS Zones` and input your server name as your wish like `malik.net.id` also create reverse `205.43.168.192.in-addr.arpa` then click `Add`

    ![](/assets/IMG/DNS4.png)

* Click `Edit` at `malik.net.id` and you'll find screen like this, configure it by yourself

    ![](/assets/IMG/DNS5.png)

* Go to `NS Records` and configure like this

    ![](/assets/IMG/DNS6.png)

* Go to `MX Records` and do it yourself like this example

    ![](/assets/IMG/DNS7.png)

* Go to `Records` and just follow this example

    ![](/assets/IMG/DNS8.png)

* After finish all steps, just hit `ok`

* Then edit reverse `205.43.168.192.in-addr.arpa` like this

    ![](/assets/IMG/DNS9.png)

    ![](/assets/IMG/DNS10.png)

    ![](/assets/IMG/DNS11.png)

* Then click `ok`

* Open terminal, then run this command

    ```
    # firewall-cmd --permanenet --add-port=53/tcp
    ```

    ```
    # firewall-cmd --permanenet --add-port=53/udp
    ```

    ```
    # firewall-cmd --reload
    ```
# Run

```
# systemctl start named
```

also run web-server and mail server

```
# systemctl start apache2
```

```
# systemctl start postfix
```

```
# systemctl start dovecot
```
# Testing

Open terminal

Run this command

```
# named-checkzone malik.net.id /var/lib/named/master/malik.net.id
```

Result

```
zone malik.net.id/IN: loaded serial 2021082701
OK
```

Then

```
# nslookup malik.net.id
```

Result

```
Server:         127.0.0.1
Address:        127.0.0.1#53

Name:   malik.net.id
Address: 192.168.43.205
Name:   malik.net.id
Address: 2404:c0:741e:720a::f0
```

Then

```
# host malik.net.id
```

Result

```
malik.net.id has address 192.168.43.205
malik.net.id has IPv6 address 2404:c0:741e:720a::f0
malik.net.id mail is handled by 3 mail.malik.net.id.
```

Then

```
# dig malik.net.id
```

Result

```

; <<>> DiG 9.16.6 <<>> malik.net.id
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 29143
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
; COOKIE: 49a35869055a2ea20100000061289b42eff26e569098f77a (good)
;; QUESTION SECTION:
;malik.net.id.                  IN      A

;; ANSWER SECTION:
malik.net.id.           172800  IN      A       192.168.43.205

;; Query time: 0 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Fri Aug 27 14:58:58 WIB 2021
;; MSG SIZE  rcvd: 85

```

open browser

```
http://malik.net.id
```

Result


![](/assets/IMG/DNS12.png)


```
http://mail.malik.net.id
```

Result

![](/assets/IMG/DNS13.png)

```
http://lib.malik.local
```

Result

![](/assets/IMG/DNS14.png)

```
http://www.malik.net.id
```

Result

![](/assets/IMG/DNS15.png)

```
http://ns.malik.net.id
```

Result

![](/assets/IMG/DNS16.png)
# Source

[https://www.vavai.com/tutorial-mudahnya-konfigurasi-dns-server-pada-opensusesles-bagian-2/](https://www.vavai.com/tutorial-mudahnya-konfigurasi-dns-server-pada-opensusesles-bagian-2/)

[https://www.unixmen.com/setup-dns-server-opensuse-13-1/](https://www.unixmen.com/setup-dns-server-opensuse-13-1/)