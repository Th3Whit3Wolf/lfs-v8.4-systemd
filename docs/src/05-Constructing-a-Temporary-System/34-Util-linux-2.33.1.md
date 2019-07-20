> # Util-linux-2.33.1
>
> The Util-linux package contains miscellaneous utility programs.
>
> **Approximate Build Time:** 1 SBU
>
> **Required Disk Space:** 147 MB

# Installation of Util-linux

Prepare Util-linux for compilation:

```sh
./configure --prefix=/tools                \
            --without-python               \
            --disable-makeinstall-chown    \
            --without-systemdsystemunitdir \
            --without-ncurses              \
            PKG_CONFIG=""
```

### The meaning of the configure option:

> **_--without-python_**
>
> > This switch disables using Python if it is installed on the host system. It avoids trying to build unneeded bindings.
>
> **_--disable-makeinstall-chown_**
>
> > This switch disables using the **chown** command during installation. This is not needed when installing into the /tools directory and avoids the necessity of installing as root.
>
> **_--without-ncurses_**
>
> > This switch disables using the ncurses library for the build process. This is not needed when installing into the /tools directory and avoids problems on some host distros.
>
> **_--without-systemdsystemunitdir_**
>
> > On systems that use systemd, the package tries to install a systemd specific file to a non-existent directory in /tools. This switch disables the unnecessary action.
>
> **_PKG_CONFIG=""_**
>
> > Setting this environment variable prevents adding unneeded features that may be available on the host. Note that the location shown for setting this environment variable is different from other LFS sections where variables are set preceding the command. This location is shown to demonstrate an alternative way of setting an environment variable when using configure.

Compile the package:

```sh
make
```

Install the package:

```sh
make install
```

> Details on this package are located in [Section 6.75.3, “Contents of Util-linux”](../06-Installing-Basic-System-Software/75-Util-linux-2.33.1.md).
