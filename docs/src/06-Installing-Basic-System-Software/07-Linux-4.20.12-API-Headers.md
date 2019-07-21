> # Linux-4.20.12 API Headers
>
> The Linux API Headers (in linux-4.20.12.tar.xz) expose the kernel's API for use by Glibc.
>
> **Approximate Build Time:** 0.1 SBU
>
> **Required Disk Space:** 941 MB

# Installation of Linux API Headers

The Linux kernel needs to expose an Application Programming Interface (API) for the system's C library (Glibc in LFS) to use. This is done by way of sanitizing various C header files that are shipped in the Linux kernel source tarball.

Make sure there are no stale files and dependencies lying around from previous activity:

```sh
make mrproper
```

Now extract the user-visible kernel headers from the source. They are placed in an intermediate local directory and copied to the needed location because the extraction process removes any existing files in the target directory. There are also some hidden files used by the kernel developers and not needed by LFS that are removed from the intermediate directory.

```sh
make INSTALL_HDR_PATH=dest headers_install
find dest/include \( -name .install -o -name ..install.cmd \) -delete
cp -rv dest/include/* /usr/include
```

> ## Contents of Linux API Headers
>
> **Installed Headers:** /usr/include/asm/_.h, /usr/include/asm-generic/_.h, /usr/include/drm/_.h, /usr/include/linux/_.h, /usr/include/misc/_.h, /usr/include/mtd/_.h, /usr/include/rdma/_.h, /usr/include/scsi/_.h, /usr/include/sound/_.h, /usr/include/video/_.h, and /usr/include/xen/\*.h
>
> **Installed Directories:** /usr/include/asm, /usr/include/asm-generic, /usr/include/drm, /usr/include/linux, /usr/include/misc, /usr/include/mtd, /usr/include/rdma, /usr/include/scsi, /usr/include/sound, /usr/include/video, and /usr/include/xen
>
> | Installed                     | Description                       |
> | :---------------------------- | :-------------------------------- |
> | /usr/include/asm/\*.h         | The Linux API ASM Headers         |
> | /usr/include/asm-generic/\*.h | The Linux API ASM Generic Headers |
> | /usr/include/drm/\*.h         | The Linux API DRM Headers         |
> | /usr/include/linux/\*.h       | The Linux API Linux Headers       |
> | /usr/include/mtd/\*.h         | The Linux API MTD Headers         |
> | /usr/include/rdma/\*.h        | The Linux API RDMA Headers        |
> | /usr/include/scsi/\*.h        | The Linux API SCSI Headers        |
> | /usr/include/sound/\*.h       | The Linux API Sound Headers       |
> | /usr/include/video/\*.h       | The Linux API Video Headers       |
> | /usr/include/xen/\*.h         | The Linux API Xen Headers         |
