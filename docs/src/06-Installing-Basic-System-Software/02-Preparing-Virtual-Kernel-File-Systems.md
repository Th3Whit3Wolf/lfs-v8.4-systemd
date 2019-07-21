# Preparing Virtual Kernel File Systems

Various file systems exported by the kernel are used to communicate to and from the kernel itself. These file systems are virtual in that no disk space is used for them. The content of the file systems resides in memory.

Begin by creating directories onto which the file systems will be mounted:

```sh
mkdir -pv $LFS/{dev,proc,sys,run}
```

## Creating Initial Device Nodes

When the kernel boots the system, it requires the presence of a few device nodes, in particular the `console` and `null` devices. The device nodes must be created on the hard disk so that they are available before **udevd** has been started, and additionally when Linux is started with _init=/bin/bash_. Create the devices by running the following commands:

```sh
mknod -m 600 $LFS/dev/console c 5 1
mknod -m 666 $LFS/dev/null c 1 3
```

## Mounting and Populating /dev

The recommended method of populating the `/dev` directory with devices is to mount a virtual filesystem (such as _tmpfs_) on the `/dev` directory, and allow the devices to be created dynamically on that virtual filesystem as they are detected or accessed. Device creation is generally done during the boot process by Udev. Since this new system does not yet have Udev and has not yet been booted, it is necessary to mount and populate `/dev` manually. This is accomplished by bind mounting the host system's `/dev` directory. A bind mount is a special type of mount that allows you to create a mirror of a directory or mount point to some other location. Use the following command to achieve this:

```sh
mount -v --bind /dev $LFS/dev
```

## Mounting Virtual Kernel File Systems

Now mount the remaining virtual kernel filesystems:

```sh
mount -vt devpts devpts $LFS/dev/pts -o gid=5,mode=620
mount -vt proc proc $LFS/proc
mount -vt sysfs sysfs $LFS/sys
mount -vt tmpfs tmpfs $LFS/run
```

### The meaning of the mount options for devpts:

> **_gid=5_**
>
> > This ensures that all devpts-created device nodes are owned by group ID 5. This is the ID we will use later on for the _tty_ group. We use the group ID instead of a name, since the host system might use a different ID for its _tty_ group.
>
> **_mode=0620_**
>
> > This ensures that all devpts-created device nodes have mode 0620 (user readable and writable, group writable). Together with the option above, this ensures that devpts will create device nodes that meet the requirements of grantpt(), meaning the Glibc pt_chown helper binary (which is not installed by default) is not necessary.

In some host systems, `/dev/shm` is a symbolic link to `/run/shm`. The /run tmpfs was mounted above so in this case only a directory needs to be created.

```sh
if [ -h $LFS/dev/shm ]; then
 mkdir -pv $LFS/$(readlink $LFS/dev/shm)
fi
```
