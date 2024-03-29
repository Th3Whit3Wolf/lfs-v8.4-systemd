# Changing Ownership

> **Note**
>
> > The commands in the remainder of this book must be performed while logged in as user _root_ and no longer as user _lfs_. Also, double check that **\$LFS** is set in _root_'s environment.

Currently, the `\$LFS/tools` directory is owned by the user _lfs_, a user that exists only on the host system. If the `\$LFS/tools` directory is kept as is, the files are owned by a user ID without a corresponding account. This is dangerous because a user account created later could get this same user ID and would own the `\$LFS/tools` directory and all the files therein, thus exposing these files to possible malicious manipulation.

To avoid this issue, you could add the _lfs_ user to the new LFS system later when creating the `/etc/passwd` file, taking care to assign it the same user and group IDs as on the host system. Better yet, change the ownership of the `\$LFS/tools` directory to user _root_ by running the following command:

```sh
chown -R root:root $LFS/tools
```

Although the `$LFS/tools` directory can be deleted once the LFS system has been finished, it can be retained to build additional LFS systems _of the same book version_. How best to backup `$LFS/tools` is a matter of personal preference.

> **Caution**
>
> > If you intend to keep the temporary tools for use in building future LFS systems, **_now_** is the time to back them up. Subsequent commands in chapter 6 will alter the tools currently in place, rendering them useless for future builds.
