> # Diffutils-3.7
>
> The Diffutils package contains programs that show the differences between files or directories.
>
> **Approximate Build Time:** 0.2 SBU
>
> **Required Disk Space:** 26 MB

# Installation of Diffutils

Prepare Diffutils for compilation:

```sh
./configure --prefix=/tools
```

Compile the package:

```sh
make
```

Compilation is now complete. As discussed earlier, running the test suite is not mandatory for the temporary tools here in this chapter. To run the Diffutils test suite anyway, issue the following command:

```sh
make check
```

Install the package:

```sh
make install
```

> Details on this package are located in [Section 6.56.2, “Contents of Diffutils”](../06-Installing-Basic-System-Software/56-Diffutils-3.7.md).
