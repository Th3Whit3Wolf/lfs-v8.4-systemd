> # MPFR-4.0.2
>
> The MPFR package contains functions for multiple precision math.
>
> **Approximate Build Time:** 1.0 SBU
>
> **Required Disk Space:** 37 MB

# Installation of MPFR

Prepare MPFR for compilation:

```sh
./configure --prefix=/usr        \
            --disable-static     \
            --enable-thread-safe \
            --docdir=/usr/share/doc/mpfr-4.0.2
```

Compile the package and generate the HTML documentation:

```sh
make
make html
```

> **IMPORTANT**
>
> > The test suite for MPFR in this section is considered critical. Do not skip it under any circumstances.

To test the results, issue:

```sh
make check
```

Install the package and its documentation:

```sh
make install
make install-html
```

> ## Contents of MPFR
>
> **Installed Programs:** File
>
> **Installed Libraries:** libmagic.so
>
> **Installed Directories:** /usr/share/doc/mpfr-4.0.2
>
> | Installed | Description                                |
> | :-------- | :----------------------------------------- |
> | libmpfr   | Contains multiple-precision math functions |
