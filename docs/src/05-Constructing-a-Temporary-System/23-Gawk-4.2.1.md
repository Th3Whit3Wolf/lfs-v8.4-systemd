> # Gawk-4.2.1
>
> The Gawk package contains programs for manipulating text files.
>
> **Approximate Build Time:** 0.2 SBU
>
> **Required Disk Space:** 43 MB

# Installation of Gawk

Prepare Gawk for compilation:

```sh
./configure --prefix=/tools
```

Compile the package:

```sh
make
```

Compilation is now complete. As discussed earlier, running the test suite is not mandatory for the temporary tools here in this chapter. To run the Gawk test suite anyway, issue the following command:

```sh
make check
```

Install the package:

```sh
make install
```

> Details on this package are located in [Section 6.57.2, “Contents of Gawk”](../06-Installing-Basic-System-Software/57-Gawk-4.2.1.md).
