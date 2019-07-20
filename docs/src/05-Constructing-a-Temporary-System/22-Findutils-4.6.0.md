> # Findutils-4.6.0
>
> The Findutils package contains programs to find files. These programs are provided to recursively search through a directory tree and to create, maintain, and search a database (often faster than the recursive find, but unreliable if the database has not been recently updated).
>
> **Approximate Build Time:** 0.3 SBU
>
> **Required Disk Space:** 36 MB

# Installation of Findutils

First, make some fixes required by glibc-2.28:

```sh
sed -i 's/IO_ftrylockfile/IO_EOF_SEEN/' gl/lib/*.c
sed -i '/unistd/a #include <sys/sysmacros.h>' gl/lib/mountlist.c
echo "#define _IO_IN_BACKUP 0x100" >> gl/lib/stdio-impl.h
```

Prepare Findutils for compilation:

```sh
./configure --prefix=/tools
```

Compile the package:

```sh
make
```

Compilation is now complete. As discussed earlier, running the test suite is not mandatory for the temporary tools here in this chapter. To run the Findutils test suite anyway, issue the following command:

```sh
make check
```

Install the package:

```sh
make install
```

> Details on this package are located in [Section 6.58.2, “Contents of Findutils”](../06-Installing-Basic-System-Software/58-Findutils-4.6.0.md).
