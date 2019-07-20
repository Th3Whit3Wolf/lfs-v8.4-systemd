> # Patch-2.7.6
>
> The Patch package contains a program for modifying or creating files by applying a “patch” file typically created by the diff program.
>
> **Approximate Build Time:** 0.2 SBU
>
> **Required Disk Space:** 12 MB

# Installation of Patch

Prepare Patch for compilation:

```sh
./configure --prefix=/tools
```

Compile the package:

```sh
make
```

Compilation is now complete. As discussed earlier, running the test suite is not mandatory for the temporary tools here in this chapter. To run the Patch test suite anyway, issue the following command:

```sh
make check
```

Install the package:

```sh
make install
```

> Details on this package are located in [Section 6.67.2, “Contents of Patch”](../06-Installing-Basic-System-Software/67-Patch-2.7.6.md).
