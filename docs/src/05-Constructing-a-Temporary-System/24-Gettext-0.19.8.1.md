> # Gettext-0.19.8.1
>
> The Gettext package contains utilities for internationalization and localization. These allow programs to be compiled with NLS (Native Language Support), enabling them to output messages in the user's native language.
>
> **Approximate Build Time:** 0.9 SBU
>
> **Required Disk Space:** 173 MB

# Installation of Gettext

For our temporary set of tools, we only need to build and install three programs from Gettext.

Prepare Gettext for compilation:

```sh
cd gettext-tools
EMACS="no" ./configure --prefix=/tools --disable-shared
```

### The meaning of the configure option:

> **_EMACS="no"_**
>
> > This prevents the configure script from determining where to install Emacs Lisp files as the test is known to hang on some hosts.
>
> **_--disable-shared_**
>
> > We do not need to install any of the shared Gettext libraries at this time, therefore there is no need to build them.

Compile the package:

```sh
make -C gnulib-lib
make -C intl pluralx.c
make -C src msgfmt
make -C src msgmerge
make -C src xgettext
```

As only three programs have been compiled, it is not possible to run the test suite without compiling additional support libraries from the Gettext package. It is therefore not recommended to attempt to run the test suite at this stage.

Install the **msgfmt**, **msgmerge**, and **xgettext** programs:

```sh
cp -v src/{msgfmt,msgmerge,xgettext} /tools/bin
```

> Details on this package are located in [Section 6.47.2, “Contents of Gettext”](../06-Installing-Basic-System-Software/47-Gettext-0.19.8.1.md).
