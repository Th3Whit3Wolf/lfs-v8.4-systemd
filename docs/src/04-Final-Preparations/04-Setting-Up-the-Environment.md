# Setting Up the Environment

Set up a good working environment by creating two new startup files for the **bash** shell. While logged in as user _lfs_, issue the following command to create a new `.bash_profile:`

```sh
cat > ~/.bash_profile << "EOF"
exec env -i HOME=$HOME TERM=$TERM PS1='\u:\w\$ ' /bin/bash
EOF
```

When logged on as user _lfs_, the initial shell is usually a _login_ shell which reads the `/etc/profile` of the host (probably containing some settings and environment variables) and then `.bash_profile`. The **exec env -i.../bin/bash** command in the `.bash_profile` file replaces the running shell with a new one with a completely empty environment, except for the **HOME**, **TERM**, and **PS1** variables. This ensures that no unwanted and potentially hazardous environment variables from the host system leak into the build environment. The technique used here achieves the goal of ensuring a clean environment.

The new instance of the shell is a _non-login_ shell, which does not read the `/etc/profile` or `.bash_profile` files, but rather reads the `.bashrc` file instead. Create the `.bashrc`file now:

```sh
cat > ~/.bashrc << "EOF"
set +h
umask 022
LFS=/mnt/lfs
LC_ALL=POSIX
LFS_TGT=$(uname -m)-lfs-linux-gnu
PATH=/tools/bin:/bin:/usr/bin
export LFS LC_ALL LFS_TGT PATH
EOF
```

The **set +h** command turns off **bash**'s hash function. Hashing is ordinarily a useful feature—**bash** uses a hash table to remember the full path of executable files to avoid searching the **PATH** time and again to find the same executable. However, the new tools should be used as soon as they are installed. By switching off the hash function, the shell will always search the **PATH** when a program is to be run. As such, the shell will find the newly compiled tools in `\$LFS/tools` as soon as they are available without remembering a previous version of the same program in a different location.

Setting the user file-creation mask (umask) to 022 ensures that newly created files and directories are only writable by their owner, but are readable and executable by anyone (assuming default modes are used by the `open(2)` system call, new files will end up with permission mode 644 and directories with mode 755).

The **LFS** variable should be set to the chosen mount point.

The **LC_ALL** variable controls the localization of certain programs, making their messages follow the conventions of a specified country. Setting **LC_ALL** to “POSIX” or “C” (the two are equivalent) ensures that everything will work as expected in the chroot environment.

The **LFS_TGT** variable sets a non-default, but compatible machine description for use when building our cross compiler and linker and when cross compiling our temporary toolchain. More information is contained in [Section 5.2, “Toolchain Technical Notes”](../05-Constructing-a-Temporary-System/02-Toolchain-Technical-Notes.md).

By putting `/tools/bin` ahead of the standard **PATH**, all the programs installed in [Chapter 5](../05-Constructing-a-Temporary-System/index.md) are picked up by the shell immediately after their installation. This, combined with turning off hashing, limits the risk that old programs are used from the host when the same programs are available in the chapter 5 environment.

Finally, to have the environment fully prepared for building the temporary tools, source the just-created user profile:

```sh
source ~/.bash_profile
```
