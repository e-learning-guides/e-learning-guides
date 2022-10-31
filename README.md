![](img/e-learning-guides-logo.png)

TODO: intro text

# Contents

## E-Learning Systems

- [Moodle and STACK](moodle/README.md)
- Ilias

## Operating Systems

- Unix
- Virtualization:
  - Xen Hypervisor

# About this documentation

If not explicitly mentioned, listings represent `bash` commands. Example

```
cd /home/
```

# Unix Commands

> Author(s): [Andreas Schwenk (TH Köln)](https://www.th-koeln.de/personen/andreas.schwenk/)

| Command | Description                     |
| ------- | ------------------------------- |
| `cd`    | Change directory                |
| `pwd`   | Print present working directory |
| `ls`    | List directory contents         |

# Debian 11

> Author(s): [Andreas Schwenk (TH Köln)](https://www.th-koeln.de/personen/andreas.schwenk/)

## Installation

native installation vs virtualization

We assume you are `root`. Otherwise, write `sudo` before the commands belor.

# OpenSSH

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

# Virtualization

## Xen Hypervisor

# Ilias

> Author(s): [Andreas Schwenk (TH Köln)](https://www.th-koeln.de/personen/andreas.schwenk/)
