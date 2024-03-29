# Toolchain Technical Notes

This section explains some of the rationale and technical details behind the overall build method. It is not essential to immediately understand everything in this section. Most of this information will be clearer after performing an actual build. This section can be referred to at any time during the process.

The overall goal of [Chapter 5](./index.md) is to produce a temporary area that contains a known-good set of tools that can be isolated from the host system. By using **chroot**, the commands in the remaining chapters will be contained within that environment, ensuring a clean, trouble-free build of the target LFS system. The build process has been designed to minimize the risks for new readers and to provide the most educational value at the same time.

> **Note**
>
> > Before continuing, be aware of the name of the working platform, often referred to as the target triplet. A simple way to determine the name of the target triplet is to run the **config.guess** script that comes with the source for many packages. Unpack the Binutils sources and run the script: `./config.guess` and note the output. For example, for a 32-bit Intel processor the output will be _i686-pc-linux-gnu_. On a 64-bit system it will be _x86_64-pc-linux-gnu_.
>
> > Also be aware of the name of the platform's dynamic linker, often referred to as the dynamic loader (not to be confused with the standard linker ld that is part of Binutils). The dynamic linker provided by Glibc finds and loads the shared libraries needed by a program, prepares the program to run, and then runs it. The name of the dynamic linker for a 32-bit Intel machine will be `ld-linux.so.2` (`ld-linux-x86-64.so.2` for 64-bit systems). A sure-fire way to determine the name of the dynamic linker is to inspect a random binary from the host system by running: **readelf -l \<name of binary> | grep interpreter** and noting the output. The authoritative reference covering all platforms is in the `shlib-versions` file in the root of the Glibc source tree.

Some key technical points of how the [Chapter 5](./index.md) build method works:

- Slightly adjusting the name of the working platform, by changing the "vendor" field target triplet by way of the **LFS_TGT** variable, ensures that the first build of Binutils and GCC produces a compatible cross-linker and cross-compiler. Instead of producing binaries for another architecture, the cross-linker and cross-compiler will produce binaries compatible with the current hardware.

- The temporary libraries are cross-compiled. Because a cross-compiler by its nature cannot rely on anything from its host system, this method removes potential contamination of the target system by lessening the chance of headers or libraries from the host being incorporated into the new tools. Cross-compilation also allows for the possibility of building both 32-bit and 64-bit libraries on 64-bit capable hardware.

- Careful manipulation of the GCC source tells the compiler which target dynamic linker will be used.

Binutils is installed first because the **configure** runs of both GCC and Glibc perform various feature tests on the assembler and linker to determine which software features to enable or disable. This is more important than one might first realize. An incorrectly configured GCC or Glibc can result in a subtly broken toolchain, where the impact of such breakage might not show up until near the end of the build of an entire distribution. A test suite failure will usually highlight this error before too much additional work is performed.

Binutils installs its assembler and linker in two locations, `/tools/bin` and `/tools/\$LFS_TGT/bin`. The tools in one location are hard linked to the other. An important facet of the linker is its library search order. Detailed information can be obtained from ld by passing it the --verbose flag. For example, an **ld --verbose | grep SEARCH** will illustrate the current search paths and their order. It shows which files are linked by **ld** by compiling a dummy program and passing the _--verbose_ switch to the linker. For example, **gcc dummy.c -Wl,--verbose 2>&1 | grep succeeded** will show all the files successfully opened during the linking.

The next package installed is GCC. An example of what can be seen during its run of **configure** is:

```sh
checking what assembler to use... /tools/i686-lfs-linux-gnu/bin/as
checking what linker to use... /tools/i686-lfs-linux-gnu/bin/ld
```

This is important for the reasons mentioned above. It also demonstrates that GCC's configure script does not search the PATH directories to find which tools to use. However, during the actual operation of gcc itself, the same search paths are not necessarily used. To find out which standard linker gcc will use, run: **gcc -print-prog-name=ld**.

Detailed information can be obtained from gcc by passing it the _-v_ command line option while compiling a dummy program. For example, **gcc -v dummy.c** will show detailed information about the preprocessor, compilation, and assembly stages, including **gcc**'s included search paths and their order.

Next installed are sanitized Linux API headers. These allow the standard C library (Glibc) to interface with features that the Linux kernel will provide.

The next package installed is Glibc. The most important considerations for building Glibc are the compiler, binary tools, and kernel headers. The compiler is generally not an issue since Glibc will always use the compiler relating to the _--host_ parameter passed to its configure script; e.g. in our case, the compiler will be **i686-lfs-linux-gnu-gcc**. The binary tools and kernel headers can be a bit more complicated. Therefore, take no risks and use the available configure switches to enforce the correct selections. After the run of **configure**, check the contents of the `config.make`file in the `glibc-build` directory for all important details. Note the use of _CC="i686-lfs-gnu-gcc"_ to control which binary tools are used and the use of the _-nostdinc_ and _-isystem_ flags to control the compiler's include search path. These items highlight an important aspect of the Glibc package—it is very self-sufficient in terms of its build machinery and generally does not rely on toolchain defaults.

During the second pass of Binutils, we are able to utilize the _--with-lib-path_ configure switch to control **ld**'s library search path.

For the second pass of GCC, its sources also need to be modified to tell GCC to use the new dynamic linker. Failure to do so will result in the GCC programs themselves having the name of the dynamic linker from the host system's `/lib` directory embedded into them, which would defeat the goal of getting away from the host. From this point onwards, the core toolchain is self-contained and self-hosted. The remainder of the [Chapter 5](./index.md) packages all build against the new Glibc in `/tools`.

Upon entering the chroot environment in [Chapter 6](../06-Installing-Basic-System-Software/index.md), the first major package to be installed is Glibc, due to its self-sufficient nature mentioned above. Once this Glibc is installed into `/usr`, we will perform a quick changeover of the toolchain defaults, and then proceed in building the rest of the target LFS system.
