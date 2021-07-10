# EXT4OF: 
A prototype feature for WORM(Write Once Read Multiple) workload.

## Prerequiste
1. Add O_RDREMOTE flag to "/usr/include/x86_64-linux-gnu/bits/fcntl-linux.h"
#ifndef O_RDREMOTE
#define O_RDREMOTE  040000000
#endif

2. Compile and install linux source code

## Basic usage
1. If you want to trigger "refreshing file system metadata", please open() a file with O_RDREMOTE flag from reader server.


## Notice (Limiations)

1. Writer server must sync all written data before open a file from reader server.
2. EXT4OF only consider open path, so you must not lookup target directory using type of "stat" system call. It will destroy the file system state.
3. Please "drop caches" and reinit file system after testing.
4. Please try this on virtual machine...
5. I am not a professional software developer, and that is why the code is not of the production-level quality.

## Future work
1. mount option to trigger feature
2. Concurrency
3. I have modified VFS, ext4 layer but not modifying vfs is left for future work.


## Contact 
If you have questions, please, contact: (virtual machine setup, IPMI setting, etc.)

Daegyu Han (hdg9400 "at" skku.edu)    

Linux kernel
============

There are several guides for kernel developers and users. These guides can
be rendered in a number of formats, like HTML and PDF. Please read
Documentation/admin-guide/README.rst first.

In order to build the documentation, use ``make htmldocs`` or
``make pdfdocs``.  The formatted documentation can also be read online at:

    https://www.kernel.org/doc/html/latest/

There are various text files in the Documentation/ subdirectory,
several of them using the Restructured Text markup notation.

Please read the Documentation/process/changes.rst file, as it contains the
requirements for building and running the kernel, and information about
the problems which may result by upgrading your kernel.
