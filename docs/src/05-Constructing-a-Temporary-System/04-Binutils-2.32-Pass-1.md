> # Binutils-2.32 - Pass 1
>
> The Binutils package contains a linker, an assembler, and other tools for handling object files.
>
> **Approximate Build Time:** 1 SBU
>
> **Required Disk Space:** 580 MB

# Installation of Cross Binutils

> **Note**
>
> > Go back and re-read the notes in the previous section. Understanding the notes labeled important will save you a lot of problems later.

It is important that Binutils be the first package compiled because both Glibc and GCC perform various tests on the available linker and assembler to determine which of their own features to enable.

The Binutils documentation recommends building Binutils in a dedicated build directory:

```sh
mkdir -v build
cd       build
```

> **Note**
>
> > In order for the SBU values listed in the rest of the book to be of any use, measure the time it takes to build this package from the configuration, up to and including the first install. To achieve this easily, wrap the commands in a **time** command like this: **time { ./configure ... && ... && make install; }**.

> **Note**
>
> > The approximate build SBU values and required disk space in Chapter 5 does not include test suite data.

### Now prepare Binutils for compilation:

```sh
../configure --prefix=/tools            \
             --with-sysroot=$LFS        \
             --with-lib-path=/tools/lib \
             --target=$LFS_TGT          \
             --disable-nls              \
             --disable-werror
```

### The meaning of the configure options:

> **_--prefix=/tools_**
>
> > This tells the configure script to prepare to install the Binutils programs in the /tools directory.
>
> **_--with-sysroot=\$LFS_**
>
> > For cross compilation, this tells the build system to look in \$LFS for the target system libraries as needed.
>
> **_--with-lib-path=/tools/lib_**
>
> > This specifies which library path the linker should be configured to use.
>
> **_--target=\$LFS_TGT_**
>
> > Because the machine description in the **LFS_TGT** variable is slightly different than the value returned by the **config.guess** script, this switch will tell the **configure** script to adjust Binutil's build system for building a cross linker.
>
> **_--disable-nls_**
>
> > This disables internationalization as i18n is not needed for the temporary tools.
>
> **_--disable-werror_**
>
> > This prevents the build from stopping in the event that there are warnings from the host's compiler.

Continue with compiling the package:

```sh
make
```

Compilation is now complete. Ordinarily we would now run the test suite, but at this early stage the test suite framework (Tcl, Expect, and DejaGNU) is not yet in place. The benefits of running the tests at this point are minimal since the programs from this first pass will soon be replaced by those from the second.

If building on x86_64, create a symlink to ensure the sanity of the toolchain:

```sh
case $(uname -m) in
  x86_64) mkdir -v /tools/lib && ln -sv lib /tools/lib64 ;;
esac
```

Install the package:

```sh
make install
```

> Details on this package are located in [Section 6.16.2, “Contents of Binutils"](../06-Installing-Basic-System-Software/16-Binutils-2.32.md).
