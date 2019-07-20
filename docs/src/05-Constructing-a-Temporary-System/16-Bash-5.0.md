> # Bash-5.0
>
> The Bash package contains the Bourne-Again SHell.
>
> **Approximate Build Time:** 0.4 SBU
>
> **Required Disk Space:** 67 MB

# Installation of Bash

Prepare Bash for compilation:

```sh
./configure --prefix=/tools --without-bash-malloc
```

### The meaning of the configure options:

> **_--without-bash-malloc_**
>
> > This option turns off the use of Bash's memory allocation (`malloc`) function which is known to cause segmentation faults. By turning this option off, Bash will use the `malloc` functions from Glibc which are more stable.

Compile the package:

```sh
make
```

Compilation is now complete. As discussed earlier, running the test suite is not mandatory for the temporary tools here in this chapter. To run the Bash test suite anyway, issue the following command:

```sh
make tests
```

Install the package:

```sh
make install
```

Make a link for the programs that use sh for a shell:

```sh
ln -sv bash /tools/bin/sh
```

> Details on this package are located in [Section 6.34.2, “Contents of Bash”](../06-Installing-Basic-System-Software/34-Bash-5.0.md).
