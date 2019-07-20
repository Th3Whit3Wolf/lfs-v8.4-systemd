> # Perl-5.28.1
>
> The Perl package contains the Practical Extraction and Report Language.
>
> **Approximate Build Time:** 1.6 SBU
>
> **Required Disk Space:** 275 MB

# Installation of Perl

Prepare Perl for compilation:

```sh
sh Configure -des -Dprefix=/tools -Dlibs=-lm -Uloclibpth -Ulocincpth
```

### The meaning of the Configure options:

> **_-des_**
>
> > This is a combination of three options: -d uses defaults for all items; -e ensures completion of all tasks; -s silences non-essential output.
>
> **_-Uloclibpth amd -Ulocincpth_**
>
> > These entries undefine variables that cause the configuration to search for locally installed components that may exist on the host system.

Build the package:

```sh
make
```

Although Perl comes with a test suite, it would be better to wait until it is installed in the next chapter.

Only a few of the utilities and libraries need to be installed at this time:

```sh
cp -v perl cpan/podlators/scripts/pod2man /tools/bin
mkdir -pv /tools/lib/perl5/5.28.1
cp -Rv lib/\* /tools/lib/perl5/5.28.1
```

> Details on this package are located in [Section 6.40.2, “Contents of Perl”](../06-Installing-Basic-System-Software/40-Perl-5.28.1.md).
