# Entering the Chroot Environment

It is time to enter the chroot environment to begin building and installing the final LFS system. As user _root_, run the following command to enter the realm that is, at the moment, populated with only the temporary tools:

```sh
chroot "$LFS" /tools/bin/env -i \
    HOME=/root                  \
    TERM="$TERM"                \
    PS1='(lfs chroot) \u:\w\$ ' \
    PATH=/bin:/usr/bin:/sbin:/usr/sbin:/tools/bin \
    /tools/bin/bash --login +h
```

The _-i_ option given to the **env** command will clear all variables of the chroot environment. After that, only the **HOME**, **TERM**, **PS1**, and **PATH** variables are set again. The **_TERM=\$TERM_** construct will set the **TERM** variable inside chroot to the same value as outside chroot. This variable is needed for programs like **vim** and **less** to operate properly. If other variables are needed, such as **CFLAGS** or **CXXFLAGS**, this is a good place to set them again.

From this point on, there is no need to use the **LFS** variable anymore, because all work will be restricted to the LFS file system. This is because the Bash shell is told that \$LFS is now the root (/) directory.

Notice that `/tools/bin` comes last in the **PATH**. This means that a temporary tool will no longer be used once its final version is installed. This occurs when the shell does not “remember” the locations of executed binaries—for this reason, hashing is switched off by passing the _+h_ option to **bash**.

Note that the **bash** prompt will say `I have no name!` This is normal because the `/etc/passwd` file has not been created yet.

> **Note**
>
> > It is important that all the commands throughout the remainder of this chapter and the following chapters are run from within the chroot environment. If you leave this environment for any reason (rebooting for example), ensure that the virtual kernel filesystems are mounted as explained in [Section 6.2.2, “Mounting and Populating /dev”](./02-Preparing-Virtual-Kernel-File-Systems.md) and [Section 6.2.3, “Mounting Virtual Kernel File Systems”](./02-Preparing-Virtual-Kernel-File-Systems.md) and enter chroot again before continuing with the installation.
