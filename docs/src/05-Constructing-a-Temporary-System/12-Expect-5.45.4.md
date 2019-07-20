> # Expect-5.45.4
>
> The Expect package contains a program for carrying out scripted dialogues with other interactive programs.
>
> **Approximate Build Time:** 0.1 SBU
>
> **Required Disk Space:** 3.9 MB

# Installation of Expect

First, force Expect's configure script to use `/bin/stty` instead of a `/usr/local/bin/stty` it may find on the host system. This will ensure that our test suite tools remain sane for the final builds of our toolchain:

```sh
cp -v configure{,.orig}
sed 's:/usr/local/bin:/bin:' configure.orig > configure
```

Now prepare Expect for compilation:

```sh
./configure --prefix=/tools \
 --with-tcl=/tools/lib \
 --with-tclinclude=/tools/include
```

### The meaning of the configure options:

> **_--with-tcl=/tools/lib_**
>
> > This ensures that the configure script finds the Tcl installation in the temporary tools location instead of possibly locating an existing one on the host system.
>
> **_--with-tclinclude=/tools/include_**
>
> > This explicitly tells Expect where to find Tcl's internal headers. Using this option avoids conditions where configure fails because it cannot automatically discover the location of Tcl's headers.

Build the package:

```sh
make
```

Compilation is now complete. As discussed earlier, running the test suite is not mandatory for the temporary tools here in this chapter. To run the Expect test suite anyway, issue the following command:

```sh
make test
```

Note that the Expect test suite is known to experience failures under certain host conditions that are not within our control. Therefore, test suite failures here are not surprising and are not considered critical.

Install the package:

```sh
make SCRIPTS="" install
```

### The meaning of the make parameter:

> **_SCRIPTS=""_**
>
> > This prevents installation of the supplementary Expect scripts, which are not needed.

> ## Contents of Expect
>
> **Installed Programs:** expect
>
> **Installed Library:** libexpect-5.45.so
>
> | Installed         | Descriptions                                                                                                          |
> | :---------------- | --------------------------------------------------------------------------------------------------------------------- |
> | **expect**        | Communicates with other interactive programs according to a script                                                    |
> | libexpect-5.45.so | Contains functions that allow Expect to be used as a Tcl extension or to be used directly from C or C++ (without Tcl) |
