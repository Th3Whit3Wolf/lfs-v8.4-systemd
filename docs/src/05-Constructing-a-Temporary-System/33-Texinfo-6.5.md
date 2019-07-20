> # Texinfo-6.5
>
> The Texinfo package contains programs for reading, writing, and converting info pages.
>
> **Approximate Build Time:** 0.3 SBU
>
> **Required Disk Space:** 104 MB

# Installation of Texinfo

Prepare Texinfo for compilation:

```sh
./configure --prefix=/tools
```

> **Note**
>
> > As part of the configure process, a test is made that indicates an error for TestXS_la-TestXS.lo. This is not relevant for LFS and should be ignored.

Compile the package:

```sh
make
```

Compilation is now complete. As discussed earlier, running the test suite is not mandatory for the temporary tools here in this chapter. To run the Texinfo test suite anyway, issue the following command:

```sh
make check
```

Install the package:

```sh
make install
```

> Details on this package are located in [Section 6.70.2, “Contents of Texinfo”](../06-Installing-Basic-System-Software/70-Texinfo-6.5.md).
