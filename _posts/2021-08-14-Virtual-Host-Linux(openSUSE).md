before you do this configuration, you should configure [DNS Server](https://mmalikhidayatulloh.github.io/2021-08-14-DNS-Server-openSUSE-with-YaST/) first.

# Make configuration

make configuration file, name of configuration as your wish like `malik.conf` but this file is copy file from `vhost.template`. to make like this you can use command

```
cp /etc/apache2/vhosts.d/vhost.template /etc/apache2/vhosts.d/malik.conf
```

# Edit configuration

In this case i want to make vhost for my mail server. So i customize configuration file like this

```
<VirtualHost *:80>
    #ServerAdmin webmaster@dummy-host.example.com
    ServerAdmin webmaster@malik.net.id
    #ServerName dummy-host.example.com
    ServerName www.malik.net.id


    # DocumentRoot: The directory out of which you will serve your
    # documents. By default, all requests are taken from this directory, but
    # symbolic links and aliases may be used to point to other locations.
    # DocumentRoot /srv/www/vhosts/dummy-host.example.com
    DocumentRoot /srv/www/htdocs/

[....]

</VirtualHost>

#######################
#   My Config
#######################

<VirtualHost *:80>
ServerName mail.malik.net.id
DocumentRoot "/srv/www/htdocs/mail"
<Directory "/srv/www/htdocs/mail">
<IfModule mod_rewrite>
Require all granted
</IfModule>
</Directory>

</VirtualHost>
<VirtualHost *:80>
ServerName lib.malik.net.id
DocumentRoot "/srv/www/htdocs/library"
<Directory "/srv/www/htdocs/library">
Options all
</Directory>
</VirtualHost>

```

# Restart Apache

```
# systemctl restart apache2
```

# Open Browser

```
http://mail.malik.local
```

![](/assets/IMG/DNS13.png)

```
http://lib.malik.local
```

![](/assets/IMG/DNS14.png)