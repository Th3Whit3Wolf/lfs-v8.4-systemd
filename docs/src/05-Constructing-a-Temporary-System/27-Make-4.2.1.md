> # Make-4.2.1
>
> The Make package contains a program for compiling packages.
>
> **Approximate Build Time:** 0.1 SBU
>
> **Required Disk Space:** 13 MB

# Installation of Make

First, work around an error caused by glibc-2.27 and later:

```sh
sed -i '211,217 d; 219,229 d; 232 d' glob/glob.c
```

Prepare Make for compilation:

```sh
./configure --prefix=/tools --without-guile
```

### The meaning of the configure option:

> **_--without-guile_**
>
> > This ensures that Make-4.2.1 won't link against Guile libraries, which may be present on the host system, but won't be available within the **chroot** environment in the next chapter.

Compile the package:

```sh
make
```

Compilation is now complete. As discussed earlier, running the test suite is not mandatory for the temporary tools here in this chapter. To run the Make test suite anyway, issue the following command:

```sh
make check
```

Install the package:

```sh
make install
```

> Details on this package are located in [Section 6.66.2, “Contents of Make”](../06-Installing-Basic-System-Software/66-Make-4.2.1.md).
