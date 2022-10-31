![](img/e-learning-guides-logo.png)

[Home](https://github.com/e-learning-guides)

# DEBIAN

> Author(s): [Andreas Schwenk (TH Köln)](https://www.th-koeln.de/personen/andreas.schwenk/)

Debian 11 can be used as reliable operating system for e-learning servers.
This guide describes the installation and basic usage of Debian 11.

- [Installation](#install)
- [Package Manager](#pm)
- [Web Server](#pm)
- [References](#ref)

# [Commands](#cmd)

# Installation

native installation vs virtualization

We assume you are `root`. Otherwise, write `sudo` before the commands belor.

# Package Manager

package manager: `apt`.

- Installation of a package:

```
apt install PACKAGE_NAME
```

- Deinstallation/removal of a package:

```
apt remove PACKAGE_NAME
```

Prevent the system to sleep:

```bash
systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target
```

# Web Server

## OpenSSH

```bash
apt install openssh-server
```

If user `root` should be allowed to log in, edit the configuration file:

```bash
nano /etc/ssh/sshd_config
```

Add the following line:

```
PermitRootLogin yes
```

> **Info** Restart the SSH server to apply changes:

```bash
systemctl restart ssh
```

## SSL

Lets Encrypt

```bash
apt install snapd
snap install core
snap refresh core
snap install --classic certbot
ln -s /snap/bin/certbot /usr/bin/certbot
certbot --apache
certbot renew --dry-run
```

Add renewal script to crontab:

```bash
crontab -e
```

Add the following line:

```
0 1 * * * /usr/bin/certbot renew
```

#

![](img/logo-th-koeln.png)
