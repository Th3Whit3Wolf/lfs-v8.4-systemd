# Table of Contents

- [Preface](./00-preface/index.md)

  - [Foreword](./00-preface/01-Foreword.md)
  - [Audience](./00-preface/02-Audience.md)
  - [LFS Target Architectures](./00-preface/03-LFS-Target-Architectures.md)
  - [LFS and Standards](./00-preface/04-LFS-and-Standards.md)
  - [Rationale for Packages in the Book](./00-preface/05-Rationale-for-Packages-in-the-Book.md)
  - [Prerequisites](./00-preface/06-Prerequisites.md)
  - [Typography](./00-preface/07-Typography.md)
  - [Structure](./00-preface/08-Structure.md)
  - [Errata](./00-preface/09-Errata.md)

- [Introduction](./01-introduction/index.md)

  - [How to Build an LFS System](./01-introduction/01-How-to-Build-an-LFS-System.md)
  - [What's new since the last release](./01-introduction/02-Whats-new-since-the-last-release.md)
  - [Changelog](./01-introduction/03-Changelog.md)
  - [Resources](./01-introduction/04-Resources.md)
  - [Help](./01-introduction/05-Help.md)

- [Preparing the Host System](./02-Preparing-the-Host-System/index.md)

  - [Introduction](./02-Preparing-the-Host-System/01-Introduction.md)
  - [Host System Requirements](./02-Preparing-the-Host-System/02-Host-System-Requirements.md)
  - [Building LFS in Stages](./02-Preparing-the-Host-System/03-Building-LFS-in-Stages.md)
  - [Creating a New Partition](./02-Preparing-the-Host-System/04-Creating-a-New-Partition.md)
  - [Creating a File System on the Partition](./02-Preparing-the-Host-System/05-Creating-a-File-System-on-the-Partition.md)
  - [Setting The \$LFS Variable](./02-Preparing-the-Host-System/06-Setting-The-$LFS-Variable.md)
  - [Mounting the New Partition](./02-Preparing-the-Host-System/07-Mounting-the-New-Partition.md)

- [Packages and Patches](./03-Packages-and-Patches/index.md)

  - [Introduction](./03-Packages-and-Patches/01-Introduction.md)
  - [All Packages](./03-Packages-and-Patches/02-All-Packages.md)
  - [Needed Patches](./03-Packages-and-Patches/03-Needed-Patches.md)

- [Final Preparations](./04-Final-Preparations/index.md)

  - [Introduction](./04-Final-Preparations/01-Introduction.md)
  - [Creating the \$LFS/tools Directory](./04-Final-Preparations/02-Creating-the-$LFS-tools-Directory.md)
  - [Adding the LFS User](./04-Final-Preparations/03-Adding-the-LFS-User.md)
  - [Setting Up the Environment](./04-Final-Preparations/04-Setting-Up-the-Environment.md)
  - [About SBUs](./04-Final-Preparations/05-About-SBUs.md)
  - [About the Test Suites](./04-Final-Preparations/06-About-the-Test-Suites.md)

- [Constructing a Temporary System](./05-Constructing-a-Temporary-System/index.md)

  - [Introduction](./05-Constructing-a-Temporary-System/01-Introduction.md)
  - [Toolchain Technical Notes](./05-Constructing-a-Temporary-System/02-Toolchain-Technical-Notes.md)
  - [General Compilation Instructions](./05-Constructing-a-Temporary-System/03-General-Compilation-Instructions.md)
  - [Binutils-2.32 - Pass 1](./05-Constructing-a-Temporary-System/04-Binutils-2.32-Pass-1.md)
  - [GCC-8.2.0 - Pass 1](./05-Constructing-a-Temporary-System/05-GCC-8.2.0-Pass-1.md)
  - [Linux-4.20.12 API Headers](./05-Constructing-a-Temporary-System/06-Linux-4.20.12-API-Headers.md)
  - [Glibc-2.29](./05-Constructing-a-Temporary-System/07-Glibc-2.29.md)
  - [Libstdc++ from GCC-8.2.0](./05-Constructing-a-Temporary-System/08-Libstdc++-from-GCC-8.2.0.md)
  - [Binutils-2.32 - Pass 2](./05-Constructing-a-Temporary-System/09-Binutils-2.32-Pass-2.md)
  - [GCC-8.2.0 - Pass 2](./05-Constructing-a-Temporary-System/10-GCC-8.2.0-Pass-2.md)
  - [Tcl-8.6.9](./05-Constructing-a-Temporary-System/11-Tcl-8.6.9.md)
  - [Expect-5.45.4](./05-Constructing-a-Temporary-System/12-Expect-5.45.4.md)
  - [DejaGNU-1.6.2](./05-Constructing-a-Temporary-System/13-DejaGNU-1.6.2.md)
  - [M4-1.4.18](./05-Constructing-a-Temporary-System/14-M4-1.4.18.md)
  - [Ncurses-6.1](./05-Constructing-a-Temporary-System/15-Ncurses-6.1.md)
  - [Bash-5.0](./05-Constructing-a-Temporary-System/16-Bash-5.0.md)
  - [Bison-3.3.2](./05-Constructing-a-Temporary-System/17-Bison-3.3.2.md)
  - [Bzip2-1.0.6](./05-Constructing-a-Temporary-System/18-Bzip2-1.0.6.md)
  - [Coreutils-8.30](./05-Constructing-a-Temporary-System/19-Coreutils-8.30.md)
  - [Diffutils-3.7](./05-Constructing-a-Temporary-System/20-Diffutils-3.7.md)
  - [File-5.36](./05-Constructing-a-Temporary-System/21-File-5.36.md)
  - [Findutils-4.6.0](./05-Constructing-a-Temporary-System/22-Findutils-4.6.0.md)
  - [Gawk-4.2.1](./05-Constructing-a-Temporary-System/23-Gawk-4.2.1.md)
  - [Gettext-0.19.8.1](./05-Constructing-a-Temporary-System/24-Gettext-0.19.8.1.md)
  - [Grep-3.3](./05-Constructing-a-Temporary-System/25-Grep-3.3.md)
  - [Gzip-1.10](./05-Constructing-a-Temporary-System/26-Gzip-1.10.md)
  - [Make-4.2.1](./05-Constructing-a-Temporary-System/27-Make-4.2.1.md)
  - [Patch-2.7.6](./05-Constructing-a-Temporary-System/28-Patch-2.7.6.md)
  - [Perl-5.28.1](./05-Constructing-a-Temporary-System/29-Perl-5.28.1.md)
  - [Python-3.7.2](./05-Constructing-a-Temporary-System/30-Python-3.7.2.md)
  - [Sed-4.7](./05-Constructing-a-Temporary-System/31-Sed-4.7.md)
  - [Tar-1.31](./05-Constructing-a-Temporary-System/32-Tar-1.31.md)
  - [Texinfo-6.5](./05-Constructing-a-Temporary-System/33-Texinfo-6.5.md)
  - [Util-linux-2.33.1](./05-Constructing-a-Temporary-System/34-Util-linux-2.33.1.md)
  - [Xz-5.2.4](./05-Constructing-a-Temporary-System/35-Xz-5.2.4.md)
  - [Stripping](./05-Constructing-a-Temporary-System/36-Stripping.md)
  - [Changing Ownership](./05-Constructing-a-Temporary-System/37-Changing-Ownership.md)

- [Installing Basic System Software](./06-Installing-Basic-System-Software/index.md)

  - [Introduction](./06-Installing-Basic-System-Software/01-Introduction.md)
  - [Preparing Virtual Kernel File Systems](./06-Installing-Basic-System-Software/02-Preparing-Virtual-Kernel-File-Systems.md)
  - [Package Management](./06-Installing-Basic-System-Software/03-Package-Management.md)
  - [Entering the Chroot Environment](./06-Installing-Basic-System-Software/04-Entering-the-Chroot-Environment.md)
  - [Creating Directories](./06-Installing-Basic-System-Software/05-Creating-Directories.md)
  - [Creating Essential Files and Symlinks](./06-Installing-Basic-System-Software/06-Creating-Essential-Files-and-Symlinks.md)
  - [Linux-4.20.12 API Headers](./06-Installing-Basic-System-Software/07-Linux-4.20.12-API-Headers.md)
  - [Man-pages-4.16](./06-Installing-Basic-System-Software/08-Man-pages-4.16.md)
  - [Glibc-2.29](./06-Installing-Basic-System-Software/09-Glibc-2.29.md)
  - [Adjusting the Toolchain](./06-Installing-Basic-System-Software/10-Adjusting-the-Toolchain.md)
  - [Zlib-1.2.11](./06-Installing-Basic-System-Software/11-Zlib-1.2.11.md)
  - [File-5.36](./06-Installing-Basic-System-Software/12-File-5.36.md)
  - [Readline-8.0](./06-Installing-Basic-System-Software/13-Readline-8.0.md)
  - [M4-1.4.18](./06-Installing-Basic-System-Software/14-M4-1.4.18.md)
  - [Bc-1.07.1](./06-Installing-Basic-System-Software/15-Bc-1.07.1.md)
  - [Binutils-2.32](./06-Installing-Basic-System-Software/16-Binutils-2.32.md)
  - [GMP-6.1.2](./06-Installing-Basic-System-Software/17-GMP-6.1.2.md)
  - [MPFR-4.0.2](./06-Installing-Basic-System-Software/18-MPFR-4.0.2.md)
  - [MPC-1.1.0](./06-Installing-Basic-System-Software/19-MPC-1.1.0.md)
  - [Shadow-4.6](./06-Installing-Basic-System-Software/20-Shadow-4.6.md)
  - [GCC-8.2.0](./06-Installing-Basic-System-Software/21-GCC-8.2.0.md)
  - [Bzip2-1.0.6](./06-Installing-Basic-System-Software/22-Bzip2-1.0.6.md)
  - [Pkg-config-0.29.2](./06-Installing-Basic-System-Software/23-Pkg-config-0.29.2.md)
  - [Ncurses-6.1](./06-Installing-Basic-System-Software/24-Ncurses-6.1.md)
  - [Attr-2.4.48](./06-Installing-Basic-System-Software/25-Attr-2.4.48.md)
  - [Acl-2.2.53](./06-Installing-Basic-System-Software/26-Acl-2.2.53.md)
  - [Libcap-2.26](./06-Installing-Basic-System-Software/27-Libcap-2.26.md)
  - [Sed-4.7](./06-Installing-Basic-System-Software/28-Sed-4.7.md)
  - [Psmisc-23.2](./06-Installing-Basic-System-Software/29-Psmisc-23.2.md)
  - [Iana-Etc-2.30](./06-Installing-Basic-System-Software/30-Iana-Etc-2.30.md)
  - [Bison-3.3.2](./06-Installing-Basic-System-Software/31-Bison-3.3.2.md)
  - [Flex-2.6.4](./06-Installing-Basic-System-Software/32-Flex-2.6.4.md)
  - [Grep-3.3](./06-Installing-Basic-System-Software/33-Grep-3.3.md)
  - [Bash-5.0](./06-Installing-Basic-System-Software/34-Bash-5.0.md)
  - [Libtool-2.4.6](./06-Installing-Basic-System-Software/35-Libtool-2.4.6.md)
  - [GDBM-1.18.1](./06-Installing-Basic-System-Software/36-GDBM-1.18.1.md)
  - [Gperf-3.1](./06-Installing-Basic-System-Software/37-Gperf-3.1.md)
  - [Expat-2.2.6](./06-Installing-Basic-System-Software/38-Expat-2.2.6.md)
  - [Inetutils-1.9.4](./06-Installing-Basic-System-Software/39-Inetutils-1.9.4.md)
  - [Perl-5.28.1](./06-Installing-Basic-System-Software/40-Perl-5.28.1.md)
  - [XML::Parser-2.44](./06-Installing-Basic-System-Software/41-XML::Parser-2.44.md)
  - [Intltool-0.51.0](./06-Installing-Basic-System-Software/42-Intltool-0.51.0.md)
  - [Autoconf-2.69](./06-Installing-Basic-System-Software/43-Autoconf-2.69.md)
  - [Automake-1.16.1](./06-Installing-Basic-System-Software/44-Automake-1.16.1.md)
  - [Xz-5.2.4](./06-Installing-Basic-System-Software/45-Xz-5.2.4.md)
  - [Kmod-26](./06-Installing-Basic-System-Software/46-Kmod-26-26tion.md)
  - [Gettext-0.19.8.1](./06-Installing-Basic-System-Software/47-Gettext-0.19.8.1.md)
  - [Libelf from Elfutils-0.176](./06-Installing-Basic-System-Software/48-Libelf-from-Elfutils-0.176.md)
  - [OpenSSL-1.1.1a](./06-Installing-Basic-System-Software/49-OpenSSL-1.1.1a-3.2.1.md)
  - [Python-3.7.2](./06-Installing-Basic-System-Software/50-Python-3.7.2.md)
  - [Ninja-1.9.0](./06-Installing-Basic-System-Software/51-Ninja-1.9.0.md)
  - [Meson-0.49.2](./06-Installing-Basic-System-Software/52-Meson-0.49.2.md)
  - [Coreutils-8.30](./06-Installing-Basic-System-Software/53-Coreutils-8.30.md)
  - [Check-0.12.0](./06-Installing-Basic-System-Software/54-Check-0.12.0.md)
  - [Diffutils-3.7](./06-Installing-Basic-System-Software/55-Diffutils-3.7.md)
  - [Gawk-4.2.1](./06-Installing-Basic-System-Software/56-Gawk-4.2.1.md)
  - [Findutils-4.6.0](./06-Installing-Basic-System-Software/57-Findutils-4.6.0.md)
  - [Groff-1.22.4](./06-Installing-Basic-System-Software/58-Groff-1.22.4.md)
  - [GRUB-2.02](./06-Installing-Basic-System-Software/59-GRUB-2.02.md)
  - [Less-530](./06-Installing-Basic-System-Software/60-Less-530.md)
  - [Gzip-1.10](./06-Installing-Basic-System-Software/61-Gzip-1.10.md)
  - [IPRoute2-4.20.0](./06-Installing-Basic-System-Software/62-IPRoute2-4.20.0.md)
  - [Kbd-2.0.4](./06-Installing-Basic-System-Software/63-Kbd-2.0.4.md)
  - [Libpipeline-1.5.1](./06-Installing-Basic-System-Software/64-Libpipeline-1.5.1.md)
  - [Make-4.2.1](./06-Installing-Basic-System-Software/65-Make-4.2.1.md)
  - [Patch-2.7.6](./06-Installing-Basic-System-Software/66-Patch-2.7.6.md)
  - [Man-DB-2.8.5](./06-Installing-Basic-System-Software/67-Man-DB-2.8.5.md)
  - [Tar-1.31](./06-Installing-Basic-System-Software/68-Tar-1.31.md)
  - [Texinfo-6.5](./06-Installing-Basic-System-Software/69-Texinfo-6.5.md)
  - [Vim-8.1](./06-Installing-Basic-System-Software/70-Vim-8.1.md)
  - [Systemd-240](./06-Installing-Basic-System-Software/71-Systemd-240.md)
  - [D-Bus-1.12.12](./06-Installing-Basic-System-Software/72-D-Bus-1.12.12.md)
  - [Procps-ng-3.3.15](./06-Installing-Basic-System-Software/73-Procps-ng-3.3.15.md)
  - [Util-linux-2.33.1](./06-Installing-Basic-System-Software/74-Util-linux-2.33.1.md)
  - [E2fsprogs-1.44.5](./06-Installing-Basic-System-Software/75-E2fsprogs-1.44.5.md)
  - [About Debugging Symbols](./06-Installing-Basic-System-Software/76-About-Debugging-Symbols.md)
  - [Stripping Again](./06-Installing-Basic-System-Software/77-Stripping-Again.md)
  - [Cleaning Up](./06-Installing-Basic-System-Software/78-Cleaning-Up.md)

- [System Configuration](./07-System-Configuration/index.md)

  - [Introduction](./07-System-Configuration/01-Introduction.md)
  - [General Network Configuration](./07-System-Configuration/02-General-Network-Configuration.md)
  - [Overview of Device and Module Handling](./07-System-Configuration/03-Overview-of-Device-and-Module-Handling.md)
  - [Managing Devices](./07-System-Configuration/04-Managing-Devices.md)
  - [Configuring the system clock](./07-System-Configuration/05-Configuring-the-system-clock.md)
  - [Configuring the Linux Console](./07-System-Configuration/06-Configuring-the-Linux-Console.md)
  - [Configuring the System Locale](./07-System-Configuration/07-Configuring-the-System-Locale.md)
  - [Creating the /etc/inputrc File](./07-System-Configuration/08-Creating-the-slash/etc-slash-inputrc-File.md)
  - [Creating the /etc/shells File](./07-System-Configuration/09-Creating-the-slash-etc-slash-shells-File.md)
  - [Systemd Usage and Configuration](./07-System-Configuration/10-Systemd-Usage-and-Configuration.md)

- [Making the LFS System Bootable](./08-Making-the-LFS-System-Bootable/index.md)

  - [Introduction](./08-Making-the-LFS-System-Bootable/01-Introduction.md)
  - [Introduction](./08-Making-the-LFS-System-Bootable/02-Creating-the-slash-etc-slash-fstab-File.md)
  - [Linux-4.20.12](./08-Making-the-LFS-System-Bootable/03-Linux-4.20.12.md)
  - [Using GRUB to Set Up the Boot Process](./08-Making-the-LFS-System-Bootable/04-Using-GRUB-to-Set-Up-the-Boot-Process.md)

- [The End](./09-The-End/index.md)

  - [The End](./09-The-End/01-The-End.md)
  - [Get Counted](./09-The-End/02-Get-Counted.md)
  - [Rebooting the System](./09-The-End/03-Rebooting-the-System.md)
  - [What Now?](./09-The-End/04-What-Now.md)

- [Appendices](./10-Appendices/index.md)

  - [Acronyms and Terms](./10-Appendices/01-Acronyms-and-Terms.md)
  - [Acknowledgments](./10-Appendices/02-Acknowledgments.md)
  - [Dependencies](./10-Appendices/03-Dependencies.md)
  - [LFS Licenses](./10-Appendices/04-LFS-Licenses.md)