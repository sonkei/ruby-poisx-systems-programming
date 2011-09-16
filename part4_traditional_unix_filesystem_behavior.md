# Traditional Unix Filesystem Behavior

>Traditional filesystems are backed by stable storage (hard drives, SSD)
and persists across reboots and shutdowns.  Some of these are designed
for Unix and considered POSIX-compliant, while others were designed for
other operating systems and incompatible with POSIX to various degrees.

POSIX-compliant filesystems are the standard, other (including pseudo)
filesystems attempt to expose a user-interface similar to those in
POSIX-compliant filesystem.  Unfortunately this means there are
sometimes leaky, incompatible, and even dangerous abstractions
may be present.

Unix filesystems are byte-oriented.  They have no notion of encodings,
and thus cannot be case-insensitive.  They do not normalize path names
or data in any way.  The lack of conversion and normalization makes path
lookup operations fast.

In a path name, only the \0" byte is disallowed.  The "/" byte is used
to delimit directories so it may not exist in a path component itself.
Otherwise, path names may contain any other byte value (even gibberish).

Regular files will store any binary data stream without altering it in
the kernel.  Filesystem operations have no notion of "lines" and won't
convert CRLF line endings to LF or vice-versa.

There are many filesystem operations defined to be atomic in POSIX.
These atomic filesystem operations are ideal for helping multiple
processes interact with each other safely.  Unfortunately, they also
make POSIX-compliance difficult for implementations of
network/distributed filesystems.

We will cover atomic operations in detail as we progress, including
caveats for working with non-POSIX filesystems.

## License: GPLv3 (or later, at the discretion of Eric Wong) http://www.gnu.org/licenses/gpl-3.0.txt
