# General Compilation Instructions

When building packages there are several assumptions made within the instructions:

- Several of the packages are patched before compilation, but only when the patch is needed to circumvent a problem. A patch is often needed in both this and the next chapter, but sometimes in only one or the other. Therefore, do not be concerned if instructions for a downloaded patch seem to be missing. Warning messages about offset or fuzz may also be encountered when applying a patch. Do not worry about these warnings, as the patch was still successfully applied.

- During the compilation of most packages, there will be several warnings that scroll by on the screen. These are normal and can safely be ignored. These warnings are as they appear—warnings about deprecated, but not invalid, use of the C or C++ syntax. C standards change fairly often, and some packages still use the older standard. This is not a problem, but does prompt the warning.

- Check one last time that the LFS environment variable is set up properly:

```sh
echo $LFS
```

Make sure the output shows the path to the LFS partition's mount point, which is `/mnt/lfs`, using our example.

- Finally, two important items must be emphasized:

> **Important**
>
> > The build instructions assume that the Host System Requirements, including symbolic links, have been set properly:
>
> - **bash** is the shell in use.
> - **sh** is a symbolic link to **bash**.
> - `/usr/bin/awk` is a symbolic link to **gawk**.
> - `/usr/bin/yacc` is a symbolic link to **bison** or a small script that executes **bison**.

> **Important**
>
> > 1. Place all the sources and patches in a directory that will be accessible from the chroot environment such as `/mnt/lfs/sources/`. Do **_not_** put sources in `/mnt/lfs/tools/`.
> > 2. Change to the sources directory.
> > 3. For each package:
> >    > - Using the **tar** program, extract the package to be built. In Chapter 5, ensure you are the **_lfs_** user when extracting the package.
> >    > - Change to the directory created when the package was extracted.
> >    > - Follow the book's instructions for building the package.
> >    > - Change back to the sources directory.
> >    > - Delete the extracted source directory unless instructed otherwise.
