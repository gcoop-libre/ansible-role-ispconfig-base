# ansible-role-ispconfig-base
Ansible base role for install and configure a ISPConfig Multiserver


# Notes on php and mcrypt

The mcrypt extension is included in PHP 5.4 through PHP 7.1. It was removed 
from PHP 7.2 and moved to an unofficial PECL extension because the mcrypt 
library is no longer maintained.

For PHP 7.2+, PHP instead uses libsodium as a cryptography library. ServerPilot 
builds PHP 7.2+ with the official libsodium extension. New PHP code should 
be written to use libsodium rather than mcrypt.


To install it in php7:

To install this extension on PHP 7.2 through 7.4, run the following commands as your server's root user:

sudo apt-get -y install gcc make autoconf libc-dev pkg-config
sudo apt-get -y install libmcrypt-dev
sudo pecl7.2-sp install --nodeps mcrypt-snapshot
When you are shown the prompt

libmcrypt prefix? [autodetect] :
Press Enter to autodetect.

Once installed, create a configuration file for the extension and restart PHP by running the following commands as root:

sudo bash -c "echo extension=mcrypt.so > /etc/php7.2-sp/conf.d/mcrypt.ini"
sudo service php7.2-fpm-sp restart


To verify:

php7.2-sp -i | grep mcrypt
