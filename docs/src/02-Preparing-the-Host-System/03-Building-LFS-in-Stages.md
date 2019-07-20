# Building LFS in Stages

LFS is designed to be built in one session. That is, the instructions assume that the system will not be shut down during the process. That does not mean that the system has to be done in one sitting. The issue is that certain procedures have to be re-accomplished after a reboot if resuming LFS at different points.

### 2.3.1. Chapters 1–4

These chapters are accomplished on the host system. When restarting, be careful of the following:

- Procedures done as the root user after Section 2.4 need to have the LFS environment variable set FOR THE ROOT USER.

### 2.3.2. Chapter 5

- The /mnt/lfs partition must be mounted.

- ALL instructions in Chapter 5 must be done by user lfs. A su - lfs needs to be done before any task in Chapter 5.

- The procedures in [Section 5.3, “General Compilation Instructions”](../05-Constructing-a-Temporary-System/03-General-Compilation-Instructions.md) are critical. If there is any doubt about installing a package, ensure any previously expanded tarballs are removed, re-extract the package files, and complete all instructions in that section.

### 2.3.3. Chapters 6–8

- The `/mnt/lfs` partition must be mounted.

- When entering chroot, the LFS environment variable must be set for root. The LFS variable is not used otherwise.

- The virtual file systems must be mounted. This can be done before or after entering chroot by changing to a host virtual terminal and, as root, running the commands in [Section 6.2.2, “Mounting and Populating /dev”](../06-Installing-Basic-System-Software/02-Preparing-Virtual-Kernel-File-Systems.md) and[ Section 6.2.3, “Mounting Virtual Kernel File Systems”](../06-Installing-Basic-System-Software/02-Preparing-Virtual-Kernel-File-Systems.md).
