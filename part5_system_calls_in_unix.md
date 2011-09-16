# System Calls in Unix

As mentioned before, syscalls are the interface user space interacts
with kernel space.  When a user space application makes a syscall,
it is telling the kernel to execute code on its behalf.

Ruby itself provides global "syscall" method on many platforms.  It is
useful for learning and experimentation, but not recommended for general
use as it is fragile and non-portable.   There is usually no need to use
this method as many useful syscalls are already provided+wrapped by Ruby
methods

For a user space application to make a system call: architecture and
OS-dependent code must be invoked.  At the lowest (userspace) levels
this is implemented in non-portable assembly code.

Fortunately, most system calls are already provided as wrappers by the
system C library (libc) so they appear to user space as portable C
functions.  Ruby itself wraps these C functions as Ruby methods.  Even
non-C Ruby implementations are likely to call these C functions in libc
(rather than implement the non-portable assembly themselves).

Thus:

>IO.pipe in Ruby is a wrapper for the pipe(3) C function which
in turn wraps the pipe(2) system call.

>You may not find the pipe(3) manpage because pipe(3) is a very thin
wrapper for the pipe(2) syscall and the pipe(2) manpage is equivalent.

## License: GPLv3 (or later, at the discretion of Eric Wong) http://www.gnu.org/licenses/gpl-3.0.txt
