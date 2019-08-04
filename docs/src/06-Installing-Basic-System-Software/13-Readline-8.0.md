> # Readline-8.0
>
> The Readline package is a set of libraries that offers command-line editing and history capabilities.
>
> **Approximate Build Time:** 0.1 SBU
>
> **Required Disk Space:** 15 MB

# Installation of Readline

Reinstalling Readline will cause the old libraries to be moved to \<libraryname>.old. While this is normally not a problem, in some cases it can trigger a linking bug in ldconfig. This can be avoided by issuing the following two seds:

```sh
sed -i '/MV.*old/d' Makefile.in
sed -i '/{OLDSUFF}/c:' support/shlib-install
```

Prepare Readline for compilation:

```sh
./configure --prefix=/usr    \
            --disable-static \
            --docdir=/usr/share/doc/readline-8.0
```

Compile the package:

```sh
make SHLIB_LIBS="-L/tools/lib -lncursesw"
```

### The meaning of the make option:

> **SHLIB_LIBS="-L/tools/lib -lncursesw"**
>
> > This option forces Readline to link against the libncursesw library.

This package does not come with a test suite.

Install the package:

```sh
make SHLIB_LIBS="-L/tools/lib -lncursesw" install
```

Now move the dynamic libraries to a more appropriate location and fix up some permissions and symbolic links:

```sh
mv -v /usr/lib/lib{readline,history}.so.* /lib
chmod -v u+w /lib/lib{readline,history}.so.*
ln -sfv ../../lib/$(readlink /usr/lib/libreadline.so) /usr/lib/libreadline.so
ln -sfv ../../lib/$(readlink /usr/lib/libhistory.so ) /usr/lib/libhistory.so
```

If desired, install the documentation:

install -v -m644 doc/\*.{ps,pdf,html,dvi} /usr/share/doc/readline-8.0

> ## Contents of Readline
>
> **Installed Libraries:** libhistory.so and libreadline.so
>
> **Installed Directories:** /usr/include/readline, /usr/share/readline, and /usr/share/doc/readline-8.0
>
> | Installed   | Description                                                                                      |
> | :---------- | :----------------------------------------------------------------------------------------------- |
> | libhistory  | Provides a consistent user interface for recalling lines of history                              |
> | libreadline | Provides a set of commands for manipulating text entered in an interactive session of a program. |
