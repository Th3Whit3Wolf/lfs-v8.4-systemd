> # Glibc-2.29
>
> The Glibc package contains the main C library. This library provides the basic routines for allocating memory, searching directories, opening and closing files, reading and writing files, string handling, pattern matching, arithmetic, and so on.
>
> **Approximate Build Time:** 5.1 SBU
>
> **Required Disk Space:** 885 MB

# Installation of Glibc

The Glibc documentation recommends building Glibc in a dedicated build directory:

```sh
mkdir -v build
cd       build
```

Next, prepare Glibc for compilation:

```sh
../configure                             \
      --prefix=/tools                    \
      --host=$LFS_TGT                    \
      --build=$(../scripts/config.guess) \
      --enable-kernel=3.2                \
      --with-headers=/tools/include
```

### The meaning of the configure options:

> **_--host=$LFS_TGT, --build=$(../scripts/config.guess)_**
>
> > The combined effect of these switches is that Glibc's build system configures itself to cross-compile, using the cross-linker and cross-compiler in `/tools`.
>
> **_--enable-kernel=3.2_**
>
> > This tells Glibc to compile the library with support for 3.2 and later Linux kernels. Workarounds for older kernels are not enabled.
>
> **_--with-headers=/tools/include_**
>
> > This tells Glibc to compile itself against the headers recently installed to the tools directory, so that it knows exactly what features the kernel has and can optimize itself accordingly.

During this stage the following warning might appear:

```sh
configure: WARNING:
*** These auxiliary programs are missing or
*** incompatible versions: msgfmt
*** some features will be disabled.
*** Check the INSTALL file for required versions.
```

The missing or incompatible **msgfmt** program is generally harmless. This **msgfmt** program is part of the Gettext package which the host distribution should provide.

> **Note**
>
> > There have been reports that this package may fail when building as a "parallel make". If this occurs, rerun the make command with a "-j1" option.

Compile the package:

```sh
make
```

Install the package:

```sh
make install
```

> **Caution**
>
> > At this point, it is imperative to stop and ensure that the basic functions (compiling and linking) of the new toolchain are working as expected. To perform a sanity check, run the following commands:
> >
> > ```
> > echo 'int main(){}' > dummy.c
> > $LFS_TGT-gcc dummy.c
> > readelf -l a.out | grep ': /tools'
> > ```
> >
> > If everything is working correctly, there should be no errors, and the output of the last command will be of the form:
> >
> > ```sh
> > [Requesting program interpreter: /tools/lib64/ld-linux-x86-64.so.2]
> > ```
> >
> > Note that for 32-bit machines, the interpreter name will be /tools/lib/ld-linux.so.2.
>
> > If the output is not shown as above or there was no output at all, then something is wrong. Investigate and retrace the steps to find out where the problem is and correct it. This issue must be resolved before continuing on.
>
> > Once all is well, clean up the test files:
> >
> > ```sh
> > rm -v dummy.c a.out
> > ```

> **Note**
>
> > Building Binutils in the section after next will serve as an additional check that the toolchain has been built properly. If Binutils fails to build, it is an indication that something has gone wrong with the previous Binutils, GCC, or Glibc installations.

> Details on this package are located in [Section 6.9.3, “Contents of Glibc”](../06-Installing-Basic-System-Software/09-Glibc-2.29.md).
