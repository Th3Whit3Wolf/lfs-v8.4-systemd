> # Gzip-1.10
>
> The Gzip package contains programs for compressing and decompressing files.
>
> **Approximate Build Time:** 0.1 SBU
>
> **Required Disk Space:** 10 MB

# Installation of Gzip

Prepare Gzip for compilation:

```sh
./configure --prefix=/tools
```

Compile the package:

```sh
make
```

Compilation is now complete. As discussed earlier, running the test suite is not mandatory for the temporary tools here in this chapter. To run the Gzip test suite anyway, issue the following command:

```sh
make check
```

Install the package:

```sh
make install
```

> Details on this package are located in [Section 6.62.2, “Contents of Gzip”](../06-Installing-Basic-System-Software/62-Gzip-1.10.md).
