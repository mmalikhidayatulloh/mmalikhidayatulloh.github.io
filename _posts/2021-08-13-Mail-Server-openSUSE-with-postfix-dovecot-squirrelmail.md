The following command use super user(root).

# Remove Sendmail
```
zypper rm -n sendmail
```

# Set DNS

follow this link [DNS Server OpenSUSE]()
# Install Postfix

```
zypper in postfix
```

# Configure postfix

```
vim /etc/postfix/main.cf
```

```
# uncomment myhostname at line 102

myhostname = mail.malik.net.id

# uncomment mydomain at line 111
mydomain = malik.net.id

# uncomment myorigin at line 128
myorigin = $mydomain

# uncomment inet_interfaces = all at line 142
inet_interfaces = all

# uncomment inet_protokols = ipv4 at line 709
inet_protokols = all

# uncomment mydestinations at line 714
mydestinations = $myhostname, localhost.$mydomain, localhost, $mydomain

# uncomment mynetworks at line 290
mynetworks = 192.168.43.0/24, 127.0.0.0/8

# uncomment home_mailbox at line 446
home_mailbox = Maildir/
```

then save and exit

# restart postfix

```
systemctl restart postfix
```

# Add user

```
useradd --create-home suse
passwd ******
```

# Install telnet

```
zypper in -y telnet
```

# Test via telnet

```
telnet malik.net.id smtp
```

output

```
Trying ::1...
Connected to localhost.
Escape character is '^]'.
220 localhost ESMTP
```
type

```
ehlo malik.net.id
```

result
```
250-localhost
250-PIPELINING
250-SIZE
250-ETRN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250-DSN
250-SMTPUTF8
250 CHUNKING
```

type
```
mailfrom:malik
```

result
```
250 2.1.0 Ok
```

type
```
rcpt to:suse
```

result

```
250 2.1.0 Ok
```

to input mail message

```
data
```

result

```
354 End data with <CR><LF>.<CR><LF>
```

then input mail message, like

```
hello
.
```

use dot (.) to complete message

result

```
250 2.0.0 Ok: queued as EF9CB16065A
```

to quit

```
quit
```

result

```
221 2.0.0 Bye
Connection closed by foreign host.
You have new mail in /home/malik/Maildir
```

# Cek email

```
ls /home/malik/Maildir/new/
```

# Install Dovecot

```
zypper in -y dovecot
```

# Configure dovecot

```
vim /etc/dovecot/dovecot.conf 
```
uncomment line 24
```
protocols = imap pop3 lmtp # submission
```

Edit file /etc/dovecot/conf.d/10-auth.conf file

```
vim /etc/dovecot/conf.d/10-auth.conf
```

set like this

```
disable_plaintext_auth = yes
```

# Start dovecot

```
systemctl start dovecot
```

# Testing dovecot

```
telnet malik.net.id pop3
```

result

```
Trying ::1...
Connected to localhost.
Escape character is '^]'.
+OK Dovecot ready.
```

login

```
user malik
+OK
pass *********
+OK Logged in.
retr 1
+OK 2388 octets
```

then quit

```
quit
+OK Logging out.
Connection closed by foreign host.
```

# Install Squirrelmail

search squirrelmail using https://pkgs.org/ then follow installation instruction

# configuration squirrelmail

```
cd /srv/www/htdocs/squirrelmail/config
./conf.pl
```

result

```
SquirrelMail Configuration : Read: config.php
Config version 1.4.0; SquirrelMail version 1.5.2 [SVN]
---------------------------------------------------------
Main Menu --
1.  Organization Preferences
2.  Server Settings
3.  Folder Defaults
4.  General Options
5.  User Interface
6.  Address Books
7.  Message of the Day (MOTD)
8.  Plugins
9.  Database
10. Language settings
11. Tweaks

D.  Set pre-defined settings for specific IMAP servers

C   Turn color on
S   Save data
Q   Quit

Command >> 
```

In this case i change organization name become `Home` then save

```
SquirrelMail Configuration : Read: config.php
Config version 1.4.0; SquirrelMail version 1.5.2 [SVN]
---------------------------------------------------------
Organization Preferences
1.  Organization Name      : Home
2.  Organization Logo      : ../images/sm_logo.png
3.  Org. Logo Width/Height : (0/0)
4.  Organization Title     : SquirrelMail $version
5.  Signout Page           : 
6.  Top Frame              : _top
7.  Provider link          : http://www.squirrelmail.org/
8.  Provider link text     : 

R   Return to Main Menu
C   Turn color on
S   Save data
Q   Quit

Command >> s

Data saved in config.php



Done activating plugins; registration data saved in plugin_hooks.php

Press enter to continue...
```

then return to main menu by hit `R`

Next is server setting like this

```
SquirrelMail Configuration : Read: config.php
Config version 1.4.0; SquirrelMail version 1.5.2 [SVN]
---------------------------------------------------------
Server Settings

General
-------
1.  Domain                 : localhost
2.  Invert Time            : false
3.  Sendmail or SMTP       : SMTP

A.  Update IMAP Settings   : localhost:143 (courier)
B.  Update SMTP Settings   : localhost:25

R   Return to Main Menu
C   Turn color on
S   Save data
Q   Quit

Command >> 
```

hit `Q` to quit

# Create sqirrelmail vhost

follow [this link](https://mmalikhidayatulloh.github.io/2021-08-14-Virtual-Host-Linux(openSUSE)/)

Then restart apache2

```
a2enmod rewrite
a2enmod mod_access_compat
systemctl restart apache2
```

# Open browser

```
http://mail.malik.net.id
```

![](/assets/IMG/DNS13.png)

login with your ordinary username and password

# Source

[https://www.unixmen.com/setup-local-mail-server-using-postfix-dovecot-squirrelmail-opensuse-13-x/](https://www.unixmen.com/setup-local-mail-server-using-postfix-dovecot-squirrelmail-opensuse-13-x/)