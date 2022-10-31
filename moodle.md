![](img/e-learning-guides-logo.png)

[Home](https://github.com/e-learning-guides)

# MOODLE 4

> Author(s): [Andreas Schwenk (TH Köln)](https://www.th-koeln.de/personen/andreas.schwenk/)

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

# [Optimization](#opt)
