> # Binutils-2.32 - Pass 2
>
> The Binutils package contains a linker, an assembler, and other tools for handling object files.
>
> **Approximate Build Time:** 1.1 SBU
>
> **Required Disk Space:** 598 MB

# Installation of Binutils

Create a separate build directory again:

```sh
 mkdir -v build
cd       build
```

Prepare Binutils for compilation:

```sh
CC=$LFS_TGT-gcc                \
AR=$LFS_TGT-ar                 \
RANLIB=$LFS_TGT-ranlib         \
../configure                   \
    --prefix=/tools            \
    --disable-nls              \
    --disable-werror           \
    --with-lib-path=/tools/lib \
    --with-sysroot
```

### The meaning of the new configure options:

> **_CC=$LFS_TGT-gcc AR=$LFS_TGT-ar RANLIB=\$LFS_TGT-ranlib_**
>
> > Because this is really a native build of Binutils, setting these variables ensures that the build system uses the cross-compiler and associated tools instead of the ones on the host system.
>
> **_--with-lib-path=/tools/lib_**
>
> > This tells the configure script to specify the library search path during the compilation of Binutils, resulting in /tools/lib being passed to the linker. This prevents the linker from searching through library directories on the host.
>
> **_--with-sysroot_**
>
> > The sysroot feature enables the linker to find shared objects which are required by other shared objects explicitly included on the linker's command line. Without this, some packages may not build successfully on some hosts.

Compile the package:

```sh
make
```

Install the package:

```sh
make install
```

Now prepare the linker for the “Re-adjusting” phase in the next chapter:

```sh
make -C ld clean
make -C ld LIB_PATH=/usr/lib:/lib
cp -v ld/ld-new /tools/bin
```

### The meaning of the make parameters:

> **_-C ld clean_**
>
> > This tells the make program to remove all compiled files in the ld subdirectory.
>
> **_-C ld LIB_PATH=/usr/lib:/lib_**
>
> > This option rebuilds everything in the ld subdirectory. Specifying the LIB_PATH Makefile variable on the command line allows us to override the default value of the temporary tools and point it to the proper final path. The value of this variable specifies the linker's default library search path. This preparation is used in the next chapter.

> Details on this package are located in [Section 6.16.2, “Contents of Binutils”](../06-Installing-Basic-System-Software/16-Binutils-2.32.md).
