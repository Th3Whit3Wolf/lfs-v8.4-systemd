> # File-5.36
>
> The File package contains a utility for determining the type of a given file or files.
>
> **Approximate Build Time:** 0.1 SBU
>
> **Required Disk Space:** 18 MB

# Installation of File

Prepare File for compilation:

```sh
./configure --prefix=/usr
```

Compile the package:

```sh
make
```

To test the results, issue:

```sh
make check
```

Install the package:

```sh
make install
```

> ## Contents of File
>
> **Installed Programs:** File
>
> **Installed Libraries:** libmagic.so
>
> | Installed | Description                                                                                                                           |
> | :-------- | :------------------------------------------------------------------------------------------------------------------------------------ |
> | **file**  | Tries to classify each given file; it does this by performing several tests—file system tests, magic number tests, and language tests |
> | libmagic  | Contains routines for magic number recognition, used by the **file** program                                                          |
