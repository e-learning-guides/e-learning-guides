![](img/e-learning-guides-logo.png)

[Home](https://github.com/e-learning-guides)

# MOODLE 4

> Author(s): [Andreas Schwenk (TH Köln)](https://www.th-koeln.de/personen/andreas.schwenk/)    
[Heiko Knospe](https://www.th-koeln.de/personen/heiko.knospe/)

This guide describes the installation and optimization of Moodle 4.

- [Base Installation](#base)
- [STACK Installation](#stack)
- [Optimizations](#opt)

# [Base Installation](#base)

Set up a base operating system. Visit our [Debian](TODO) guide for detailed information.

We assume to use an `Apache` web server.

```bash
apt install apache2 php git wget mariadb-server sudo curl php-curl php-zip php-mysql php-xml php-mbstring php-gd php-intl php-xmlrpc php-soap php-yaml gnuplot make texinfo python python3 locate texlive ghostscript
```

# [Database](#db)   
Use mysql or mariadb
```bash 
mysql -u root -p
mysql> CREATE DATABASE moodle DEFAULT CHARACTER SET utf8 COLLATE utf8_unicode_ci;
mysql> CREATE USER moodleuser@localhost IDENTIFIED BY 'yourpassword';
mysql> GRANT SELECT,INSERT,UPDATE,DELETE,CREATE,CREATE TEMPORARY TABLES,DROP,INDEX,ALTER ON moodle.* TO moodleuser@localhost;
mysql> FLUSH PRIVILEGES;
mysql> quit
```

# [Crontab](#crontab)
Default Moodle:
```bash
crontab -e 
*/5 * * * * wget -q -O /dev/null http://localhost/admin/cron.php
```
Modified:
```bash
* * * * * sudo -u <webuser> /usr/bin/php <moodledir>/admin/cli/cron.php > <dir>/moodle-cron-log.txt 2>&1
25 3 * * * <dir>/moodle-backup.sh >> <dir>/moodle-backup-log.txt 2>&1
```

# [Upload](#upload)
Changes in `/etc/php/7.4/apache2/php.ini`:    
```bash
post_max_size = 50M
upload_max_filesize = 50M
max_execution_time = 60
```

# [SSL/TLS](#ssl)
Apache2 sites configuration file:
```bash
SSLEngine on
SSLCertificateFile    <ssl-dir>/certs/servercert.pem
SSLCertificateKeyFile <ssl-dir>/private/serverkey.pem
SSLCertificateChainFile <ssl-dir>/certs/intermed.pem
```

# [Privacy](#sec)
Go to Site administration > Users > Permissions > Define roles.   
Click the Edit settings icon (the gear button) for the Student role.    
Filter the list by typing ‘Participants‘ in the filter field.        
Make sure you uncheck the two capabilities called View participants. By default the Course: View participants check box is ticked to Allow. Uncheck this.
Click Save changes to commit the change in Permission.

administration > Users > Manage Roles > Students. Uncheck:
moodle/user:viewdetails

# [STACK Installation](#stack)

## Maxima

TODO: LISP: `clisp` vs `sbcl`

TODO: maxima version must be supported by STACK (TODO: provide link)

```bash
apt install sbcl
```

```bash
cd ~
wget https://sourceforge.net/projects/maxima/files/Maxima-source/5.44.0-source/maxima-5.44.0.tar.gz
tar -xzvf maxima-5.44.0.tar.gz
cd maxima-5.44.0
./configure --enable-sbcl --enable-sbcl-exec
make
make install
```

Check if `maxima` is working:

```bash
maxima --version
maxima
```

Type e.g. `(1 + sqrt(2))^5;` and press enter.

## STACK

# [Optimizations](#opt)

- TODO: e.g. turn off questionpool evaluation plugin ...
- TODO: Was nun ewig dauert, ist die Auflistung von Kategorien in der Fragesammlung. In Moodle 4 werden dort Indikatoren angezeigt, wie zB “Überprüfung notwendig”, “Leichtigkeitsindex”. Insbesondere wenn man den Cache löscht, dauert es je nach Anzahl der Fragen in einer Kategorie viele Sekunden bis einige Minuten, bis die Liste angezeigt wird. Die CPU Last ist via “top” aber vernachlässigter gering. Per “iotop -oPa” (Dependancy: “apt Install texinfo”) kann man die IO-Activity in Debian sehen. Beispiel: Der Prozess “mariadb” schreibt knapp 140 MB auf die VM-Disk (siehe Screenshot im Anhang), wenn man die Fragekategorie “Potenz-/Log-/Wurzelrechnung” mit 72 Fragen öffnet. Man kann in den Plugineinstellungen im Bereich “Fragensammlungsplugins” den Punkt “Fragestatistiken” ausschalten. Dann läuft alles wieder flüssig.

#

![](img/logo-th-koeln.png)
