> # Python-3.7.2
>
> The Python 3 package contains the Python development environment. It is useful for object-oriented programming, writing scripts, prototyping large programs or developing entire applications.
>
> **Approximate Build Time:** 1.5 SBU
>
> **Required Disk Space:** 371 MB

# Installation of Python

This package first builds the Python interpreter, then some standard Python modules. The main script for building modules is written in Python, and uses hard-coded paths to the host /usr/include and /usr/lib directories. To prevent them from being used, issue:

```sh
sed -i '/def add_multiarch_paths/a \        return' setup.py
```

Prepare Python for compilation:

```sh
./configure --prefix=/tools --without-ensurepip
```

### The meaning of the configure option:

> **_--without-ensurepip_**
>
> > This switch disables the Python installer, which is not needed at this stage.

Compile the package:

```sh
make
```

Compilation is now complete. The test suite requires TK and and X Windows and cannot be run at this time.

Install the package:

```sh
make install
```

> Details on this package are located in [Section 6.51.2, “Contents of Python 3”](../06-Installing-Basic-System-Software/51-Python-3.7.2.md).
