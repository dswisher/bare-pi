# raspi3-tutorial - my version

This directory contains my work going through the [raspi-tutorial](https://github.com/bztsrc/raspi3-tutorial) by bztsrc.
I'm doing it on a Mac, using LLVM, so I've made a few changes to the `Makefile`, and I'll be doing everything in one directory.

Any errors are my responsibility, and your mileage may vary.


# Tool Chain

## QEMU

Turns out this is fairly easy, as it is available via brew:

    brew install qemu

## Cross-Compiler - LLVM

The Mac has `clang` built-in, but folks have noted issues with that, and it is lacking some of
the additional tools. The version available from brew seems to work:

    brew install llvm

Note that installs in a directory that is not in the path, so as not to conflict with the built-in
bits. I've put the paths in the Makefile, so I don't need to update my PATH variable.

* [source](https://embeddedartistry.com/blog/2017/2/20/installing-clangllvm-on-osx)


# [Tutorial 01](https://github.com/bztsrc/raspi3-tutorial/tree/master/01_bareminimum) - Bare Minimum

The only change I had to make was in the Makefile, to use the brew-installed LLVM tool chain.


# [Tutorial 02](https://github.com/bztsrc/raspi3-tutorial/tree/master/02_multicorec) - Multicore C

Seems to work, although I need to learn a bit more about ARM assembly to be sure. Open questions:

* What exactly is the assembly doing?
* What is the loader file (`link.ld`) doing?


# [Tutorial 03](https://github.com/bztsrc/raspi3-tutorial/tree/master/03_uart1) - UART1, Auxilary mini UART

TODO

