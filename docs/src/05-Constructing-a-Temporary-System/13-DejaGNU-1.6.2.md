> # DejaGNU-1.6.2
>
> The DejaGNU package contains a framework for testing other programs.
>
> **Approximate Build Time:** less than 0.1 SBU
>
> **Required Disk Space:** 3.2 MB

# Installation of DejaGNU

Prepare DejaGNU for compilation:

```sh
./configure --prefix=/tools
```

Build and install the package:

```sh
make install
```

To test the results, issue:

```sh
make check
```

> ## Contents of DejaGNU
>
> **Installed Programs:** runtest
>
> | Installed   | Descriptions                                                                |
> | :---------- | --------------------------------------------------------------------------- |
> | **runtest** | A wrapper script that locates the proper expect shell and then runs DejaGNU |
