![](img/e-learning-guides-logo.png)

This xxx

# Contents

- Moodle
  - STACK
- Ilias
- Unix
- Virtualization:
  - Xen Hypervisor

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

> `PermitRootLogin yes`

# Virtualization

## Xen Hypervisor

# Moodle

> Author(s): [Andreas Schwenk (TH Köln)](https://www.th-koeln.de/personen/andreas.schwenk/)

## Base Installation

## Optimization

## STACK Installation

# Ilias

> Author(s): [Andreas Schwenk (TH Köln)](https://www.th-koeln.de/personen/andreas.schwenk/)
