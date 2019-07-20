> # Libstdc++ from GCC-8.2.0
>
> Libstdc++ is the standard C++ library. It is needed to compile C++ code (part of GCC is written in C++), but we had to defer its installation when we built [gcc-pass1](./05-GCC-8.2.0-Pass-1) because it depends on glibc, which was not yet available in `/tools`.
>
> **Approximate Build Time:** 0.5 SBU
>
> **Required Disk Space:** 803 MB

# Installation of Target Libstdc++

> **Note**
>
> > Libstdc++ is part of the GCC sources. You should first unpack the GCC tarball and change to the `gcc-8.2.0` directory.

Create a separate build directory for Libstdc++ and enter it:

```sh
mkdir -v build
cd       build
```

Prepare Libstdc++ for compilation:

```sh
../libstdc++-v3/configure           \
    --host=$LFS_TGT                 \
    --prefix=/tools                 \
    --disable-multilib              \
    --disable-nls                   \
    --disable-libstdcxx-threads     \
    --disable-libstdcxx-pch         \
    --with-gxx-include-dir=/tools/$LFS_TGT/include/c++/8.2.0
```

### The meaning of the configure options:

> **_--host=..._**
>
> > Indicates to use the cross compiler we have just built instead of the one in `/usr/bin`.
> > **_ --disable-libstdcxx-threads_**
>
> > Since we have not yet built the C threads library, the C++ one cannot be built either.
>
> **_--disable-libstdcxx-pch_**
>
> > This switch prevents the installation of precompiled include files, which are not needed at this stage.
>
> **_--with-gxx-include-dir=/tools/\$LFS_TGT/include/c++/8.2.0_**
>
> > This is the location where the standard include files are searched by the C++ compiler. In a normal build, this information is automatically passed to the Libstdc++ configure options from the top level directory. In our case, this information must be explicitly given.

Compile libstdc++ by running:

```sh
make
```

Install the library:

```sh
make install
```

> Details on this package are located in [Section 6.21.2, “Contents of GCC”](../06-Installing-Basic-System-Software/21-GCC-8.2.0.md).
