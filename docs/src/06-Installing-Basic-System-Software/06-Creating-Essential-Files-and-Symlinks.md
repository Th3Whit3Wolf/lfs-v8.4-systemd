# Creating Essential Files and Symlinks

Some programs use hard-wired paths to programs which do not exist yet. In order to satisfy these programs, create a number of symbolic links which will be replaced by real files throughout the course of this chapter after the software has been installed:

```sh
ln -sv /tools/bin/{bash,cat,chmod,dd,echo,ln,mkdir,pwd,rm,stty,touch} /bin
ln -sv /tools/bin/{env,install,perl,printf}         /usr/bin
ln -sv /tools/lib/libgcc_s.so{,.1}                  /usr/lib
ln -sv /tools/lib/libstdc++.{a,so{,.6}}             /usr/lib

install -vdm755 /usr/lib/pkgconfig

ln -sv bash /bin/sh
```

### The purpose of each link:

> **_/bin/bash_**
>
> > Many **bash** scripts specify `/bin/bash`.
>
> **_/bin/cat_**
>
> > This pathname is hard-coded into Glibc's configure script.
>
> **_/bin/dd_**
>
> > The path to **dd** will be hard-coded into the `/usr/bin/libtool` utility.
>
> **_/bin/echo_**
>
> > This is to satisfy one of the tests in Glibc's test suite, which expects `/bin/echo`.
>
> **_/usr/bin/env_**
>
> > This pathname is hard-coded into some packages build procedures.
>
> **_/usr/bin/install_**
>
> > The path to install will be hard-coded into the `/usr/lib/bash/Makefile.inc` file.
>
> **_/bin/ln_**
>
> > The path to **ln** will be hard-coded into the `/usr/lib/perl5/5.28.1/<target-triplet>/Config_heavy.pl` file.
>
> **_/bin/pwd_**
>
> > Some **configure** scripts, particularly Glibc's, have this pathname hard-coded.
>
> **_/bin/rm_**
>
> > The path to **rm** will be hard-coded into the `/usr/lib/perl5/5.28.1/<target-triplet>/Config_heavy.pl` file.
>
> **_/bin/stty_**
>
> > This pathname is hard-coded into **Expect**, therefore it is needed for **Binutils** and **GCC** test suites to pass.
>
> **_/usr/bin/perl_**
>
> > Many **Perl** scripts hard-code this path to the **perl** program.
>
> **_/usr/lib/libgcc_s.so{,.1}_**
>
> > Glibc needs this for the pthreads library to work.
>
> **_/usr/lib/libstdc++{,.6}_**
>
> > This is needed by several tests in Glibc's test suite, as well as for C++ support in GMP.
>
> **_/bin/sh_**
>
> > Many shell scripts hard-code `/bin/sh`.

Historically, Linux maintains a list of the mounted file systems in the file `/etc/mtab`. Modern kernels maintain this list internally and exposes it to the user via the `/proc` filesystem. To satisfy utilities that expect the presence of `/etc/mtab`, create the following symbolic link:

```sh
ln -sv /proc/self/mounts /etc/mtab
```

In order for user _root_ to be able to login and for the name “root” to be recognized, there must be relevant entries in the `/etc/passwd` and `/etc/group` files.

Create the `/etc/passwd` file by running the following command:

```sh
cat > /etc/passwd << "EOF"
root:x:0:0:root:/root:/bin/bash
bin:x:1:1:bin:/dev/null:/bin/false
daemon:x:6:6:Daemon User:/dev/null:/bin/false
messagebus:x:18:18:D-Bus Message Daemon User:/var/run/dbus:/bin/false
systemd-bus-proxy:x:72:72:systemd Bus Proxy:/:/bin/false
systemd-journal-gateway:x:73:73:systemd Journal Gateway:/:/bin/false
systemd-journal-remote:x:74:74:systemd Journal Remote:/:/bin/false
systemd-journal-upload:x:75:75:systemd Journal Upload:/:/bin/false
systemd-network:x:76:76:systemd Network Management:/:/bin/false
systemd-resolve:x:77:77:systemd Resolver:/:/bin/false
systemd-timesync:x:78:78:systemd Time Synchronization:/:/bin/false
systemd-coredump:x:79:79:systemd Core Dumper:/:/bin/false
nobody:x:99:99:Unprivileged User:/dev/null:/bin/false
EOF
```

The actual password for _root_ (the “x” used here is just a placeholder) will be set later.

Create the `/etc/group` file by running the following command:

```sh
cat > /etc/group << "EOF"
root:x:0:
bin:x:1:daemon
sys:x:2:
kmem:x:3:
tape:x:4:
tty:x:5:
daemon:x:6:
floppy:x:7:
disk:x:8:
lp:x:9:
dialout:x:10:
audio:x:11:
video:x:12:
utmp:x:13:
usb:x:14:
cdrom:x:15:
adm:x:16:
messagebus:x:18:
systemd-journal:x:23:
input:x:24:
mail:x:34:
kvm:x:61:
systemd-bus-proxy:x:72:
systemd-journal-gateway:x:73:
systemd-journal-remote:x:74:
systemd-journal-upload:x:75:
systemd-network:x:76:
systemd-resolve:x:77:
systemd-timesync:x:78:
systemd-coredump:x:79:
wheel:x:97:
nogroup:x:99:
users:x:999:
EOF
```

The created groups are not part of any standard—they are groups decided on in part by the requirements of the Udev configuration in this chapter, and in part by common convention employed by a number of existing Linux distributions. In addition, some test suites rely on specific users or groups. The [Linux Standard Base](http://www.linuxbase.org) (LSB) recommends only that, besides the group _root_ with a Group ID (GID) of 0, a group _bin_ with a GID of 1 be present. All other group names and GIDs can be chosen freely by the system administrator since well-written programs do not depend on GID numbers, but rather use the group's name.

To remove the “I have no name!” prompt, start a new shell. Since a full Glibc was installed in [Chapter 5](../05-Constructing-a-Temporary-System/index.md) and the `/etc/passwd` and `/etc/group` files have been created, user name and group name resolution will now work:

```sh
exec /tools/bin/bash --login +h
```

Note the use of the _+h_ directive. This tells **bash** not to use its internal path hashing. Without this directive, **bash** would remember the paths to binaries it has executed. To ensure the use of the newly compiled binaries as soon as they are installed, the _+h_ directive will be used for the duration of this chapter.

The **login**, **agetty**, and **init** programs (and others) use a number of log files to record information such as who was logged into the system and when. However, these programs will not write to the log files if they do not already exist. Initialize the log files and give them proper permissions:

```sh
touch /var/log/{btmp,lastlog,faillog,wtmp}
chgrp -v utmp /var/log/lastlog
chmod -v 664  /var/log/lastlog
chmod -v 600  /var/log/btmp
```

The `/var/log/wtmp` file records all logins and logouts. The `/var/log/lastlog` file records when each user last logged in. The `/var/log/faillog` file records failed login attempts. The `/var/log/btmp` file records the bad login attempts.

> **Note**
>
> > The `/run/utmp` file records the users that are currently logged in. This file is created dynamically in the boot scripts.
