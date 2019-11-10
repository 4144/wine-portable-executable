## Description

This project allows to pack Wine and almost all required libraries into a single portable executable that should work on most Linux distributions. This project uses SquashFS as the container for Wine and libraries (similar to what AppImage does).

What's the benefits compared to regular Wine builds? The main benefit is that much less libraries need to be installed into system, another benefit is that SquashFS supports fast compression algorithms (such as lz4 or zstd), so Wine can launch faster and use less disk space.

The structure of portable executables (from the top the end of the file):

1. Script that mounts bundled squashfs image and runs the Wine
2. Squashfuse binary and its libraries, in case if squashfuse isn't isntalled
3. Squashfs image that contains Wine, required libraries (wine-runtime)
and custom launch script

---

## Requirements

First of all, **FUSE** is required.

And, despite almost all libraries are included into squashfs image, some basic libraries are still need to be installed. Some required libraries:

* libc6 (glibc)
* libGL (videodriver)

It's important to install both 32-bit and 64-bit versions of required libraries.

**GLIBC 2.27** or newer is required as the Runtime is a libraries from Ubuntu 18.04.

---

## How to use portable Wine executables

Root rights are **not required**!

Make a file executable and the run it. For example:

    chmod +x wine-portable-4.19-amd64.sh
    ./wine-portable-4.19-amd64.sh applications.exe

Or to run winecfg:

    ./wine-portable-4.19-amd64.sh winecfg
    
You can download ready to use portable Wine/Proton executables from the [releases](https://github.com/Kron4ek/wine-portable-executable/releases) page. **GLIBC 2.27** or newer is required for these builds.

---

## How to create portable Wine executables

Use **create_wine_portable.sh** script.

---

### Notes

This project has not been thoroughly tested, please report any problems you found.
