# Changelog

This is version 8.4-systemd of the Linux From Scratch book, dated Maarch 1, 2019. If this book is more than six months old, a newer and better version is probably already available. To find out, please check one of the [mirrors](http://www.linuxfromscratch.org/mirrors.html).

Below is a list of changes made since the previous release of the book.

**Changelog Entries:**

- 2019-03-01

  - [bdubbs] - LFS-8.4 released.

- 2019-02-25

  - [bdubbs] - Update to linux-4.20.12. Fixes [#4425](http://wiki.linuxfromscratch.org/lfs/ticket/4425).
  - [bdubbs] - Update to elfutils-0.176. Fixes [#4426](http://wiki.linuxfromscratch.org/lfs/ticket/4426).
  - [bdubbs] - Update to file-5.36. Fixes [#4429](http://wiki.linuxfromscratch.org/lfs/ticket/4429).
  - [renodr] - Add a security patch for systemd-240 to fix a PID1 crash over D-Bus. Fixes [#4428](http://wiki.linuxfromscratch.org/lfs/ticket/4428).

- 2019-02-19

  - [bdubbs] - Add an optional modification to the build procedure for ninja to allow use the the environment variable NINJAJOBS.

- 2019-02-14

  - [bdubbs] - Update to linux-4.20.8. Fixes [#4423](http://wiki.linuxfromscratch.org/lfs/ticket/4423).
  - [bdubbs] - Fix a problem when building Python in Chapter 5 where some hosts may use host dependent headers.

- 2019-02-11

  - [bdubbs] - Update to linux-4.20.7. Fixes [#4421](http://wiki.linuxfromscratch.org/lfs/ticket/4421).
  - Update to kmod-26. Fixes [#4422](http://wiki.linuxfromscratch.org/lfs/ticket/4422).

  - 2019-02-08
  - - [renodr] - Update host system requirements.

- 2019-02-06

  - [bdubbs] - Simlify instructions for glibc in Chapter 5. Thanks to Romain Geissler for the report.

- 2019-02-05

  - [bdubbs] - Update to bison-3.3.2. Fixes [#4419](http://wiki.linuxfromscratch.org/lfs/ticket/4418).
  - [bdubbs] - Update to meson-0.49.2. Fixes [#4420.](http://wiki.linuxfromscratch.org/lfs/ticket/4418)

- 2019-02-02

* [bdubbs] - Fix psmisc URL. Fixes [#4418](http://wiki.linuxfromscratch.org/lfs/ticket/4418).
* [bdubbs] - Update to binutils-2.32. Fixes [#4417](http://wiki.linuxfromscratch.org/lfs/ticket/4417).

- 2019-02-01

  - [bdubbs] - Update to bison-3.3.1. Fixes [#4412](http://wiki.linuxfromscratch.org/lfs/ticket/4412).
  - [bdubbs] - Update to glibc-2.29. Fixes [#4415](http://wiki.linuxfromscratch.org/lfs/ticket/4452).
  - [bdubbs] - Update to libpipeline-1.5.1. Fixes [#4413](http://wiki.linuxfromscratch.org/lfs/ticket/4413).
  - [bdubbs] - Update to linux-4.20.6. Fixes [#4409](http://wiki.linuxfromscratch.org/lfs/ticket/4409).
  - [bdubbs] - Update to meson-0.49.1. Fixes [#4410](http://wiki.linuxfromscratch.org/lfs/ticket/4410).
  - [bdubbs] - Update to mpfr-4.0.2. Fixes [#4416](http://wiki.linuxfromscratch.org/lfs/ticket/4416).
  - [bdubbs] - Update to ninja-1.9.0. Fixes [#4414](http://wiki.linuxfromscratch.org/lfs/ticket/4414).

- 2019-01-27

  - [pierre] - Fix a bug introduced in tar-1.31, by adding a sed to the build instructions. Also remove an obsolete comment about a failing test.

- 2019-01-20

  - [renodr] - Regenerate the systemd man pages tarball with the Non-namespaced versions of the Docbook XSL Stylesheets.

- 2019-01-27

  - [renodr] - Add a security patch for systemd-240. This fixes CVE-2018-16865 and CVE-2018-16864 (memory corruption in journald leading to stack overflows / arbitrary code execution). Apply this as soon as you can. Fixes [#4408](http://wiki.linuxfromscratch.org/lfs/ticket/4408).

- 2019-01-10

  - [bdubbs] - Update to linux-4.20.1. Fixes [#4398](http://wiki.linuxfromscratch.org/lfs/ticket/4398).
  - [bdubbs] - Update to diffutils-3.7. Fixes [#4401](http://wiki.linuxfromscratch.org/lfs/ticket/4401).
  - [bdubbs] - Update to tar-1.31. Fixes [#4402](http://wiki.linuxfromscratch.org/lfs/ticket/4402).
  - [bdubbs] - Update to man-db-2.8.5. Fixes [#4403](http://wiki.linuxfromscratch.org/lfs/ticket/4403).
  - [bdubbs] - Update to bash-5.0. Fixes [#4404](http://wiki.linuxfromscratch.org/lfs/ticket/4410).
  - [bdubbs] - Update to readline-8.0. Fixes [#4405](http://wiki.linuxfromscratch.org/lfs/ticket/4405).
  - [bdubbs] - Update to iproute2-4.20.0. Fixes [#4406](http://wiki.linuxfromscratch.org/lfs/ticket/4406).
  - [bdubbs] - Update to util-linux-2.33.1. Fixes [#4407](http://wiki.linuxfromscratch.org/lfs/ticket/4407).

- 2019-01-01

  - [bdubbs] - Update to gzip-1.10. Fixes [#4400](http://wiki.linuxfromscratch.org/lfs/ticket/4400).
  - [bdubbs] - Update to tzdata-2018i. Fixes [#4399](http://wiki.linuxfromscratch.org/lfs/ticket/4399).

- 2018-12-27

  - [bdubbs] - Update to linux-4.19.12. Fixes [#4389](http://wiki.linuxfromscratch.org/lfs/ticket/4389).
  - [bdubbs] - Update to e2fsprogs-1.44.5. Fixes [#4390](http://wiki.linuxfromscratch.org/lfs/ticket/4390).
  - [bdubbs] - Update to bison-3.2.4. Fixes [#4391](http://wiki.linuxfromscratch.org/lfs/ticket/4391).
  - [bdubbs] - Update to sed-4.7. Fixes [#4392](http://wiki.linuxfromscratch.org/lfs/ticket/4392).
  - [bdubbs] - Update to grep-3.3. Fixes [#4393](http://wiki.linuxfromscratch.org/lfs/ticket/4393).
  - [bdubbs] - Update to systemd-240. Contains a critical fix for systemd-tmpfiles (privilege escalation). Fixes [#4394](http://wiki.linuxfromscratch.org/lfs/ticket/4394).
  - [bdubbs] - Update to Python-3.7.2. Fixes [#4395](http://wiki.linuxfromscratch.org/lfs/ticket/4395).
  - [bdubbs] - Update to groff-1.22.4. Fixes [#4396](http://wiki.linuxfromscratch.org/lfs/ticket/4396).

- 2018-12-12

  - [renodr] - Add a note to libffi about optimizing for the specific CPU in use at compile time. Similar to GMP, this causes Illegal Operation errors if the installation is moved to another system.

- 2018-12-01

  - [bdubbs] - Move `/etc/bash_completions.d/grub` to a better location. Fixes [#4385](http://wiki.linuxfromscratch.org/lfs/ticket/4385).
  - [bdubbs] - Update to dejagnu-1.6.2. Fixes [#4382](http://wiki.linuxfromscratch.org/lfs/ticket/4382).
  - [bdubbs] - Update to linux-4.19.6. Fixes [#4383](http://wiki.linuxfromscratch.org/lfs/ticket/4383).
  - [bdubbs] - Update to perl-5.28.1. Fixes [#4384](http://wiki.linuxfromscratch.org/lfs/ticket/4384).

- 2018-11-25

  - [renodr] - Update to bison-3.2.2. Fixes [#4380](http://wiki.linuxfromscratch.org/lfs/ticket/4380).

- 2018-11-24

  - [dj] - Update to linux-4.19.4. Fixes [#4381](http://wiki.linuxfromscratch.org/lfs/ticket/4381).
  - [dj] - Update to systemd-239-6b4878d.
  - [dj] - Add "wheel" group to systemd groups.
  - [dj] - Add touch to the list of moved coreutils programs, and clarify necessity of the moves to meet FHS compliance.

* 2018-11-21

  - [renodr] - Add "wheel" group to satisfy systemd requirements. Fixes [#4376](http://wiki.linuxfromscratch.org/lfs/ticket/4376).
  - [renodr] - Add a sed to fix a bug in autoconf's test suite. Fixes [#4372](http://wiki.linuxfromscratch.org/lfs/ticket/4372).
  - [renodr] - Update to tcl-8.6.9. Security update. Fixes [#4375](http://wiki.linuxfromscratch.org/lfs/ticket/4375).
  - [renodr] - Update to openssl-1.1.1a. This is a security update. Fixes [#4379](http://wiki.linuxfromscratch.org/lfs/ticket/4379).
  - [renodr] - Update to systemd-239-25d1ba1. This fixes three security problems in systemd. Fixes [#4377](http://wiki.linuxfromscratch.org/lfs/ticket/4376).
  - [renodr] - Update to linux-4.19.3. Fixes [#4373](http://wiki.linuxfromscratch.org/lfs/ticket/4373).
  - [renodr] - Update to elfutils-0.175. Fixes [#4374](http://wiki.linuxfromscratch.org/lfs/ticket/4374).

* 2018-11-19

  - [bdubbs] - Update to libcap-2.26. Fixes [#4378](http://wiki.linuxfromscratch.org/lfs/ticket/4378).

* 2018-11-09

  - [bdubbs] - Update to meson-0.48.2. Fixes [#4371](http://wiki.linuxfromscratch.org/lfs/ticket/4371).
  - [bdubbs] - Update to bison-3.2.1. Fixes [#4370](http://wiki.linuxfromscratch.org/lfs/ticket/4370).

* 2018-11-06

  - [bdubbs] - Update to bison-3.2. Fixes [#4367](http://wiki.linuxfromscratch.org/lfs/ticket/4367).
  - [bdubbs] - Update to linux-4.19.1. Fixes [#4368](http://wiki.linuxfromscratch.org/lfs/ticket/4368).
  - [bdubbs] - Update to tzdata-2018g. Fixes [#4366](http://wiki.linuxfromscratch.org/lfs/ticket/4366).
  - [bdubbs] - Update to util-linux-v2.33. Fixes [#4353](http://wiki.linuxfromscratch.org/lfs/ticket/4353).

* 2018-10-29

  - [dj] - Update to gdbm-1.18.1. Fixes [#4364](http://wiki.linuxfromscratch.org/lfs/ticket/4364).
  - [dj] - Update to Python-3.7.1. Fixes [#4361](http://wiki.linuxfromscratch.org/lfs/ticket/4361).

* 2018-10-27

  - [dj] - Update to iproute2-4.19.0. Fixes [#4363](http://wiki.linuxfromscratch.org/lfs/ticket/4363).
  - [dj] - Update to file-5.35. Fixes [#4359](http://wiki.linuxfromscratch.org/lfs/ticket/4359).
  - [dj] - Update to tzdata-2018f. Fixes [#4358](http://wiki.linuxfromscratch.org/lfs/ticket/4358).
  - [dj] - Update to meson-0.48.1. Fixes [#4357](http://wiki.linuxfromscratch.org/lfs/ticket/4357).
  - [dj] - Update to linux-4.19. Fixes [#4356](http://wiki.linuxfromscratch.org/lfs/ticket/4356).

* 2018-10-10

  - [dj] - Removed incorrect link to /toold/lib64 in systemd instructions. Fixes [#4355](http://wiki.linuxfromscratch.org/lfs/ticket/4355).
  - [dj] - Added systemd-239-meson-0.48.0_fixes-1.patch to resolve build errors with meson.
  - [dj] - Update to meson-0.48.0. Fixes [#4351](http://wiki.linuxfromscratch.org/lfs/ticket/4351).
  - [dj] - Update to linux-4.18.12. Fixes [#4352](http://wiki.linuxfromscratch.org/lfs/ticket/4351).

* 2018-09-30

  - [dj] - Restore build of Util-Linux in chapter5 to avoid reciprocal dependency for Systemd.
  - [dj] - Moved installation of Util-Linux and E2fsprogs after Procps to satisfy build order in the Systemd book. This has no effect on the SysV book.

* 2018-09-20

  - [bdubbs] - Clean up of unneeded symbolic links. Reordered packages so version specific packages are built as late as possible in Chapter 6. Now building util-linux in Chapter 5 is unneeded and has been removed. Fixes [#4345](http://wiki.linuxfromscratch.org/lfs/ticket/4345) and [#4349](http://wiki.linuxfromscratch.org/lfs/ticket/4349).
  - [bdubbs] - Update to elfutils-0.174 (libelf). Fixes [#4348](http://wiki.linuxfromscratch.org/lfs/ticket/4348).
  - [bdubbs] - Update to psmisc-23.2. Fixes [#4347](http://wiki.linuxfromscratch.org/lfs/ticket/4347).
  - [bdubbs] - Update to openssl-1.1.1. Fixes [#4346](http://wiki.linuxfromscratch.org/lfs/ticket/4346).
  - [bdubbs] - Update to linux-4.18.9. Fixes [#4344](http://wiki.linuxfromscratch.org/lfs/ticket/4344).

* 2018-09-02

  - [bdubbs] - Update to bison-3.1. Fixes [#4342](http://wiki.linuxfromscratch.org/lfs/ticket/4342).
  - [bdubbs] - Update to meson-0.47.2. Fixes [#4341](http://wiki.linuxfromscratch.org/lfs/ticket/4341).
  - [bdubbs] - Update to gdbm-1.18. Fixes [#4340](http://wiki.linuxfromscratch.org/lfs/ticket/4340).
  - [bdubbs] - Update to e2fsprogs-1.44.4. Fixes [#4338](http://wiki.linuxfromscratch.org/lfs/ticket/4338).

* 2018-09-01

  - [bdubbs] - LFS-8.3 released.
