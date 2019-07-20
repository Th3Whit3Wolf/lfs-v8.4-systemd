> # Ncurses-6.1
>
> The Ncurses package contains libraries for terminal-independent handling of character screens.
>
> **Approximate Build Time:** 0.6 SBU
>
> **Required Disk Space:** 41 MB

# Installation of Ncurses

First, ensure that gawk is found first during configuration:

```sh
sed -i s/mawk// configure
```

Prepare Ncurses for compilation:

```sh
./configure --prefix=/tools \
 --with-shared \
 --without-debug \
 --without-ada \
 --enable-widec \
 --enable-overwrite
```

### The meaning of the configure options:

> **_--without-ada_**
>
> > This ensures that Ncurses does not build support for the Ada compiler which may be present on the host but will not be available once we enter the **chroot** environment.
>
> **_--enable-overwrite_**
>
> > This tells Ncurses to install its header files into `/tools/include`, instead of `/tools/include/ncurses`, to ensure that other packages can find the Ncurses headers successfully.
>
> **_--enable-widec_**
>
> > This switch causes wide-character libraries (e.g., `libncursesw.so.6.1`) to be built instead of normal ones (e.g., `libncurses.so.6.1`). These wide-character libraries are usable in both multibyte and traditional 8-bit locales, while normal libraries work properly only in 8-bit locales. Wide-character and normal libraries are source-compatible, but not binary-compatible.

Compile the package:

```sh
make
```

This package has a test suite, but it can only be run after the package has been installed. The tests reside in the test/ directory. See the README file in that directory for further details.

Install the package:

```sh
make install
ln -s libncursesw.so /tools/lib/libncurses.so
```

> Details on this package are located in [Section 6.24.2, “Contents of Ncurses”](../06-Installing-Basic-System-Software/24-Gettext-0.19.8.1.md).
