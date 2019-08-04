> # Zlib-1.2.11
>
> The Zlib package contains compression and decompression routines used by some programs.
>
> **Approximate Build Time:** less than 0.1 SBU
>
> **Required Disk Space:** 4.4 MB

# Installation of Zlib

Prepare Zlib for compilation:

```sh
./configure --prefix=/usr
```

Compile the package:

```sh
make
```

To test the results, issue:

```sh
make check
```

Install the package:

```sh
make install
```

The shared library needs to be moved to `/lib`, and as a result the `.so` file in `/usr/lib` will need to be recreated:

```sh
mv -v /usr/lib/libz.so.\* /lib
ln -sfv ../../lib/\$(readlink /usr/lib/libz.so) /usr/lib/libz.so
```

> ## Contents of Zlib
>
> **Installed Libraries:** libz.{a,so}
>
> | Installed | Description                                                            |
> | :-------- | :--------------------------------------------------------------------- |
> | libz      | Contains compression and decompression functions used by some programs |
