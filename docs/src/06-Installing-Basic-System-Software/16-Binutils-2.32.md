> # Binutils-2.32
>
> The Binutils package contains a linker, an assembler, and other tools for handling object files.
>
> **Approximate Build Time:** 6.9 SBU
>
> **Required Disk Space:** 4.9 MB

# Installation of Binutils

Verify that the PTYs are working properly inside the chroot environment by performing a simple test:

```sh
expect -c "spawn ls"
```

This command should output the following:

```sh
spawn ls
```

If, instead, the output includes the message below, then the environment is not set up for proper PTY operation. This issue needs to be resolved before running the test suites for Binutils and GCC:

```sh
The system has no more ptys.
Ask your system administrator to create more.
```

mkdir -v build
cd build

The Binutils documentation recommends building Binutils in a dedicated build directory:

Prepare Binutils for compilation:

```sh
../configure --prefix=/usr       \
             --enable-gold       \
             --enable-ld=default \
             --enable-plugins    \
             --enable-shared     \
             --disable-werror    \
             --enable-64-bit-bfd \
             --with-system-zlib
```

### The meaning of the configure parameters:

> **--enable-gold**
>
> > Build the gold linker and install it as ld.gold (along side the default linker).
> > **--enable-ld=default**
>
> > Build the original bdf linker and install it as both ld (the default linker) and ld.bfd.
>
> **--enable-plugins**
>
> > Enables plugin support for the linker.
>
> **--enable-64-bit-bfd**
>
> > Enables 64-bit support (on hosts with narrower word sizes). May not be needed on 64-bit systems, but does no harm.
>
> **--with-system-zlib**
>
> > Use the installed zlib library rather than building the included version.

Compile the package:

```sh
make tooldir=/usr
```

### The meaning of the make parameters:

> **tooldir=/usr**
>
> > Normally, the tooldir (the directory where the executables will ultimately be located) is set to \$(`exec_prefix`)/\$(`target_alias`). For example, x86_64 machines would expand that to `/usr/x86_64-unknown-linux-gnu`. Because this is a custom system, this target-specific directory in `/usr` is not required. \$(`exec_prefix`)/\$(`target_alias`) would be used if the system was used to cross-compile (for example, compiling a package on an Intel machine that generates code that can be executed on PowerPC machines).

> **IMPORTANT**
>
> > The test suite for Binutils in this section is considered critical. Do not skip it under any circumstances.

To test the results, issue:

```sh
make -k check
```

One test, debug_msg.sh, is known to fail.

Install the package:

```sh
make tooldir=/usr install
```

> ## Contents of Binutils
>
> **Installed Programs:** addr2line, ar, as, c++filt, elfedit, gprof, ld, ld.bfd, ld.gold, nm, objcopy, objdump, ranlib, readelf, size, strings, and strip
>
> **Installed Libraries:** libbfd.{a,so} and libopcodes.{a,so}
>
> **Installed Directories:** /usr/lib/ldscripts
>
> | Installed       | Description                                                                                                                                                                                                                                                                                       |
> | :-------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
> | ** addr2line ** | Translates program addresses to file names and line numbers; given an address and the name of an executable, it uses the debugging information in the executable to determine which source file and line number are associated with the address                                                   |
> | **ar**          | Creates, modifies, and extracts from archives                                                                                                                                                                                                                                                     |
> | **as**          | An assembler that assembles the output of **gcc** into object files                                                                                                                                                                                                                               |
> | **c++filt**     | Used by the linker to de-mangle C++ and Java symbols and to keep overloaded functions from clashing                                                                                                                                                                                               |
> | **elfedit**     | Updates the ELF header of ELF files                                                                                                                                                                                                                                                               |
> | **gprof**       | Displays call graph profile data                                                                                                                                                                                                                                                                  |
> | **ld**          | A linker that combines a number of object and archive files into a single file, relocating their data and tying up symbol references                                                                                                                                                              |
> | **ld.gold**     | A cut down version of ld that only supports the elf object file format                                                                                                                                                                                                                            |
> | **ld.bfd**      | Hard link to **ld**                                                                                                                                                                                                                                                                               |
> | **nm**          | Lists the symbols occurring in a given object file                                                                                                                                                                                                                                                |
> | **objcopy**     | Translates one type of object file into another                                                                                                                                                                                                                                                   |
> | **objdump**     | Displays information about the given object file, with options controlling the particular information to display; the information shown is useful to programmers who are working on the compilation tools                                                                                         |
> | **ranlib**      | Generates an index of the contents of an archive and stores it in the archive; the index lists all of the symbols defined by archive members that are relocatable object files                                                                                                                    |
> | **readelf**     | Displays information about ELF type binaries                                                                                                                                                                                                                                                      |
> | **size**        | Lists the section sizes and the total size for the given object files                                                                                                                                                                                                                             |
> | **strings**     | Outputs, for each given file, the sequences of printable characters that are of at least the specified length (defaulting to four); for object files, it prints, by default, only the strings from the initializing and loading sections while for other types of files, it scans the entire file |
> | **strip**       | Discards symbols from object files                                                                                                                                                                                                                                                                |
> | libbfd          | The Binary File Descriptor library                                                                                                                                                                                                                                                                |
> | libopcodes      | A library for dealing with opcodes—the “readable text” versions of instructions for the processor; it is used for building utilities like **objdump**                                                                                                                                             |
