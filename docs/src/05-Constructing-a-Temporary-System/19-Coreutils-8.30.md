> # Coreutils-8.30
>
> The Coreutils package contains utilities for showing and setting the basic system characteristics.
>
> **Approximate Build Time:** 0.8 SBU
>
> **Required Disk Space:** 148 MB

# Installation of Coreutils

Prepare Coreutils for compilation:

```sh
./configure --prefix=/tools --enable-install-program=hostname
```

### The meaning of the configure options:

> **_--enable-install-program=hostname_**
>
> > This enables the **hostname** binary to be built and installed – it is disabled by default but is required by the Perl test suite.

Compile the package:

```sh
make
```

Compilation is now complete. As discussed earlier, running the test suite is not mandatory for the temporary tools here in this chapter. To run the Coreutils test suite anyway, issue the following command:

```sh
make RUN_EXPENSIVE_TESTS=yes check
```

The _RUN_EXPENSIVE_TESTS=yes_ parameter tells the test suite to run several additional tests that are considered relatively expensive (in terms of CPU power and memory usage) on some platforms, but generally are not a problem on Linux.

Install the package:

```sh
make install
```

> Details on this package are located in [Section 6.54.2, “Contents of Coreutils”](../06-Installing-Basic-System-Software/54-Coreutils-8.30.md).
