# Using GRUB to Set Up the Boot Process

# Introduction

> **Warning**
>
> > Configuring GRUB incorrectly can render your system inoperable without an alternate boot device such as a CD-ROM. This section is not required to boot your LFS system. You may just want to modify your current boot loader, e.g. Grub-Legacy, GRUB2, or LILO.

Ensure that an emergency boot disk is ready to “rescue” the computer if the computer becomes unusable (un-bootable). If you do not already have a boot device, you can create one. In order for the procedure below to work, you need to jump ahead to BLFS and install **xorriso** from the [libisoburn](http://www.linuxfromscratch.org/blfs/view/8.4/multimedia/libisoburn.html) package.

```sh
cd /tmp
grub-mkrescue --output=grub-img.iso
xorriso -as cdrecord -v dev=/dev/cdrw blank=as_needed grub-img.iso
```

> **Note**
>
> > To boot LFS on host systems that have UEFI enabled, the kernel needs to have been built with the CONFIG_EFI_STUB capabality described in the previous section. However, LFS can be booted using GRUB2 without such an addition. To do this, the UEFI Mode and Secure Boot capabilities in the host system's BIOS need to be turned off. For details, see the [lfs-uefi.txt hint](http://www.linuxfromscratch.org/hints/downloads/files/lfs-uefi.txt).

# GRUB Naming Conventions

GRUB uses its own naming structure for drives and partitions in the form of (_hdn,m_), where _n_ is the hard drive number and m is the partition number. The hard drive number starts from zero, but the partition number starts from one for normal partitions and five for extended partitions. Note that this is different from earlier versions where both numbers started from zero. For example, partition `sda1` is (_hd0,1_) to GRUB and `sdb3` is (_hd1,3_). In contrast to Linux, GRUB does not consider CD-ROM drives to be hard drives. For example, if using a CD on `hdb` and a second hard drive on `hdc`, that second hard drive would still be (_hd1_).

# Setting Up the Configuration

GRUB works by writing data to the first physical track of the hard disk. This area is not part of any file system. The programs there access GRUB modules in the boot partition. The default location is `/boot/grub/`.

The location of the boot partition is a choice of the user that affects the configuration. One recommendation is to have a separate small (suggested size is 100 MB) partition just for boot information. That way each build, whether LFS or some commercial distro, can access the same boot files and access can be made from any booted system. If you choose to do this, you will need to mount the separate partition, move all files in the current `/boot` directory (e.g. the linux kernel you just built in the previous section) to the new partition. You will then need to unmount the partition and remount it as `/boot`. If you do this, be sure to update `/etc/fstab`.

Using the current lfs partition will also work, but configuration for multiple systems is more difficult.

Using the above information, determine the appropriate designator for the root partition (or boot partition, if a separate one is used). For the following example, it is assumed that the root (or separate boot) partition is `sda2`.

Install the GRUB files into `/boot/grub` and set up the boot track:

> **Warning**
>
> > The following command will overwrite the current boot loader. Do not run the command if this is not desired, for example, if using a third party boot manager to manage the Master Boot Record (MBR).

```sh
grub-install /dev/sda
```

> **Note**
>
> > If the system has been booted using UEFI, **grub-install** will try to install files for the _x86_64-efi_ target, but those files have not been installed in chapter 6. If this is the case, add `--target i386-pc` to the command above.

# Creating the GRUB Configuration File

Generate `/boot/grub/grub.cfg`:

```sh
cat > /boot/grub/grub.cfg << "EOF"
# Begin /boot/grub/grub.cfg
set default=0
set timeout=5

insmod ext2
set root=(hd0,2)

menuentry "GNU/Linux, Linux 4.20.12-lfs-8.4-systemd" {
        linux   /boot/vmlinuz-4.20.12-lfs-8.4-systemd root=/dev/sda2 ro
}
EOF
```

> **Note**
>
> > From GRUB's perspective, the kernel files are relative to the partition used. If you used a separate `/boot` partition, remove `/boot` from the above _linux_ line. You will also need to change the set _root_ line to point to the boot partition.

GRUB is an extremely powerful program and it provides a tremendous number of options for booting from a wide variety of devices, operating systems, and partition types. There are also many options for customization such as graphical splash screens, playing sounds, mouse input, etc. The details of these options are beyond the scope of this introduction.

> **Caution**
>
> > There is a command, **grub-mkconfig**, that can write a configuration file automatically. It uses a set of scripts in `/etc/grub.d/` and will destroy any customizations that you make. These scripts are designed primarily for non-source distributions and are not recommended for LFS. If you install a commercial Linux distribution, there is a good chance that this program will be run. Be sure to back up your `grub.cfg` file.
