> # Grep-3.3
>
> The Grep package contains programs for searching through files.
>
> **Approximate Build Time:** 0.2 SBU
>
> **Required Disk Space:** 24 MB

# Installation of Grep

Prepare Grep for compilation:

```sh
./configure --prefix=/tools
```

Compile the package:

```sh
make
```

Compilation is now complete. As discussed earlier, running the test suite is not mandatory for the temporary tools here in this chapter. To run the Grep test suite anyway, issue the following command:

```sh
make check
```

Install the package:

```sh
make install
```

> Details on this package are located in [Section 6.33.2, “Contents of Grep”](../06-Installing-Basic-System-Software/33-Grep-3.3.md).
