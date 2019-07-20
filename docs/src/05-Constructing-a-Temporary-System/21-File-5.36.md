> # File-5.36
>
> The File package contains a utility for determining the type of a given file or files.
>
> **Approximate Build Time:** 0.1 SBU
>
> **Required Disk Space:** 18 MB

# Installation of File

Prepare File for compilation:

```sh
./configure --prefix=/tools
```

Compile the package:

```sh
make
```

Compilation is now complete. As discussed earlier, running the test suite is not mandatory for the temporary tools here in this chapter. To run the File test suite anyway, issue the following command:

```sh
make check
```

Install the package:

```sh
make install
```

> Details on this package are located in [Section 6.12.2, “Contents of File”](../06-Installing-Basic-System-Software/12-File-5.36.md).
