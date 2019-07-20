# Adding the LFS User

When logged in as user _root_, making a single mistake can damage or destroy a system. Therefore, we recommend building the packages in this chapter as an unprivileged user. You could use your own user name, but to make it easier to set up a clean working environment, create a new user called _lfs_ as a member of a new group (also named _lfs_) and use this user during the installation process. As _root_, issue the following commands to add the new user:

```sh
groupadd lfs
useradd -s /bin/bash -g lfs -m -k /dev/null lfs
```

**The meaning of the command line options:**

> **-s /bin/bash**
>
> > This makes bash the default shell for user lfs.
>
> **-g lfs**
>
> > This option adds user lfs to group lfs.
>
> **-m**
>
> > This creates a home directory for lfs.
>
> **-k /dev/null**
>
> > This parameter prevents possible copying of files from a skeleton directory (default is /etc/skel) by changing the input location to the special null device.
>
> **lfs**
>
> > This is the actual name for the created group and user.

To log in as _lfs_ (as opposed to switching to user _lfs_ when logged in as _root_, which does not require the _lfs_ user to have a password), give _lfs_ a password:

```sh
passwd lfs
```

Grant _lfs_ full access to `$LFS/tools` by making _lfs_ the directory owner:

```sh
chown -v lfs $LFS/tools
```

If a separate working directory was created as suggested, give user _lfs_ ownership of this directory:

```sh
chown -v lfs $LFS/sources
```

Next, login as user _lfs_. This can be done via a virtual console, through a display manager, or with the following substitute user command:

```sh
su - lfs
```

The “-” instructs **su** to start a login shell as opposed to a non-login shell. The difference between these two types of shells can be found in detail in `bash(1)` and **info bash**.
