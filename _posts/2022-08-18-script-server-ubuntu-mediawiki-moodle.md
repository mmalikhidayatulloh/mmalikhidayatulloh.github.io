```
apt install -y apache2 mysql-server php libapache2-mod-php php-mysql php-curl php-json php-cgi php-curl php-gd php-mbstring php-xml php-xmlrpc php-intl
systemctl enable apache2 mariadb
systemctl start apache2 mariadb
```
```
mysql -u root
CREATE DATABASE wiki;
CREATE USER 'adminwiki'@'localhost' IDENTIFIED BY 'adminwiki';
GRANT ALL ON webdata.* TO 'adminwiki'@'localhost';
CREATE DATABASE moodle;
CREATE USER 'adminmoodle'@'localhost' IDENTIFIED BY 'adminmoodle';
GRANT ALL ON webdata.* TO 'adminmoodle'@'localhost';
SHOW DATABASES;
quit
```
```
cd /var/www/html/
git clone git://git.moodle.org/moodle.git
cd moodle
git branch -a
git branch --track MOODLE_400_STABLE origin/MOODLE_400_STABLE
git checkout MOODLE_400_STABLE
cd /var/www/html/
git clone https://gerrit.wikimedia.org/r/mediawiki/core.git --branch REL1_38 mediawiki
```
