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
    ServerAdmin webmaster@malik.local
    #ServerName dummy-host.example.com
    ServerName www.malik.local


    # DocumentRoot: The directory out of which you will serve your
    # documents. By default, all requests are taken from this directory, but
    # symbolic links and aliases may be used to point to other locations.
    # DocumentRoot /srv/www/vhosts/dummy-host.example.com
    DocumentRoot /srv/www/htdocs/

....

</VirtualHost>

###########################
# Virtual host mail server#
###########################
NameVirtualHost *:80
<VirtualHost *:80 >
ServerName mail.malik.local

DocumentRoot /srv/www/htdocs/squirrelmail
<Directory /srv/www/htdocs/squirrelmail>
    Options Indexes FollowSymLinks
    RewriteEngine On
    AllowOverride All
    DirectoryIndex index.php
    Order allow,deny
    Allow from all
</Directory>
</VirtualHost>
```

# Open Browser

```
http://mail.malik.local
```

![](/assets/IMG/Screenshot_20210814_034801.png)