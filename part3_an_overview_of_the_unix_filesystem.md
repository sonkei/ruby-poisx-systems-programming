# An Overview of the Unix Filesystem

Unix features a hierarchical filesystem visible to all running processes.  It is the primary shared namespace within a Unix system.

As you may know, the top of this namespace starts at "/" (or the root) and subdirectories may be created under it, each path component separated by "/".

Filesystems may contain other filesystems.  The root filesystem on a modern Unix system almost always contains other filesystems.

Filesystems may have several types of files: 
- directories
- symlinks
- UNIX domain sockets
- FIFOs
- character devices
- block devices
- "regular" files.

Traditional filesystems are backed by stable storage (hard drives, SSD) and persists across reboots and shutdowns.  Some of these are designed for Unix and considered POSIX-compliant, while others were designed for other operating systems and incompatible with POSIX to various degrees.

Various pseudo-filesystems exist, but they are mostly non-standardized. Among pseudo-filesystems, there are memory-only filesystems, network filesystems, proc (process information) filesystems, device filesystems, and filesystems for tuning/inspecting kernel and hardware.

Pseudo-filesystems allow Unix-based operating systems to avoid implementing system calls only useful within a limited scope..

The "everything-is-a-file" design and use of filesystems (even for non-storage tasks) allows a few system calls to be useful for multiple purposes.  This consistency improves the user experience by reducing the amount a systems programmer needs to know and also improving discoverability of the interfaces.

As the amount of system calls is relatively small, learning Unix systems programming should be easier than in other operating systems.

Plan 9 (the intended successor to Unix) takes "everything-is-a-file" more literally to further minimize the need for specialized system calls.  This Plan 9 idea (among others) is being co-opted into existing userspaces and operating systems.

## cense: GPLv3 (or later, at the discretion of Eric Wong) http://www.gnu.org/licenses/gpl-3.0.txt
