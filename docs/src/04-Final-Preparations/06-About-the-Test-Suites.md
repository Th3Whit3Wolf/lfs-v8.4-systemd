# About the Test Suites

Most packages provide a test suite. Running the test suite for a newly built package is a good idea because it can provide a “sanity check” indicating that everything compiled correctly. A test suite that passes its set of checks usually proves that the package is functioning as the developer intended. It does not, however, guarantee that the package is totally bug free.

Some test suites are more important than others. For example, the test suites for the core toolchain packages—GCC, Binutils, and Glibc—are of the utmost importance due to their central role in a properly functioning system. The test suites for GCC and Glibc can take a very long time to complete, especially on slower hardware, but are strongly recommended.

> **Note**
>
> > Experience has shown that there is little to be gained from running the test suites in [Chapter 5](../05-Constructing-a-Temporary-System/index.md). There can be no escaping the fact that the host system always exerts some influence on the tests in that chapter, often causing inexplicable failures. Because the tools built in [Chapter 5](../05-Constructing-a-Temporary-System/index.md) are temporary and eventually discarded, we do not recommend running the test suites in [Chapter 5](../05-Constructing-a-Temporary-System/index.md) for the average reader. The instructions for running those test suites are provided for the benefit of testers and developers, but they are strictly optional.

A common issue with running the test suites for Binutils and GCC is running out of pseudo terminals (PTYs). This can result in a high number of failing tests. This may happen for several reasons, but the most likely cause is that the host system does not have the devpts file system set up correctly. This issue is discussed in greater detail at [here](http://www.linuxfromscratch.org/lfs/faq.html#no-ptys).

Sometimes package test suites will fail, but for reasons which the developers are aware of and have deemed non-critical. Consult the [logs](http://www.linuxfromscratch.org/lfs/build-logs/8.4/) to verify whether or not these failures are expected. This site is valid for all tests throughout this book.
