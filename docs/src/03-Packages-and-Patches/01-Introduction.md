# Introduction

his chapter includes a list of packages that need to be downloaded in order to build a basic Linux system. The listed version numbers correspond to versions of the software that are known to work, and this book is based on their use. We highly recommend against using newer versions because the build commands for one version may not work with a newer version. The newest package versions may also have problems that require work-arounds. These work-arounds will be developed and stabilized in the development version of the book.

Download locations may not always be accessible. If a download location has changed since this book was published, [Google](http://www.google.com/) provides a useful search engine for most packages. If this search is unsuccessful, try one of the alternative means of downloading discussed at [here(http://www.linuxfromscratch.org/lfs/packages.html#packages).

Downloaded packages and patches will need to be stored somewhere that is conveniently available throughout the entire build. A working directory is also required to unpack the sources and build them. `\$LFS/sources` can be used both as the place to store the tarballs and patches and as a working directory. By using this directory, the required elements will be located on the LFS partition and will be available during all stages of the building process.

To create this directory, execute the following command, as user _root_, before starting the download session:

```sh
mkdir -v $LFS/sources
```

Make this directory writable and sticky. “Sticky” means that even if multiple users have write permission on a directory, only the owner of a file can delete the file within a sticky directory. The following command will enable the write and sticky modes:

```sh
chmod -v a+wt $LFS/sources
```

An easy way to download all of the packages and patches is by using [wget-list](http://www.linuxfromscratch.org/lfs/view/stable-systemd/wget-list) as an input to **wget**. For example:

```sh
wget --input-file=wget-list --continue --directory-prefix=$LFS/sources
```

Additionally, starting with LFS-7.0, there is a separate file, [md5sums](http://www.linuxfromscratch.org/lfs/view/stable-systemd/md5sums), which can be used to verify that all the correct packages are available before proceeding. Place that file in `\$LFS/sources` and run:

```sh
pushd $LFS/sources
md5sum -c md5sums
popd
```
