# Linux pVFS: Persistent Virtual Filesystem

pVFS enables the VFS layer to use persistent memory.

## Problem

Persistent memory enables user to persist file in a fast and fine granularity
way thanks to its byte-addressability and persistency.  With persistent memory, 
the contents written by CPU to a file becomes persistent immediately after a 
cache flush.  In contrast, the only way to persist modifications to a file in
disk is by issuing synchronization operations such as `fsync()` that performs 
I/O operations.

Currently the only way to use the persistent file semantic is to put
the file in persistent memory, which, however, makes it an expensive option.
Compared with disks, persistent memory has a higher price per bit and smaller
capacity.  Threfore, ecnomically, it costs more to put the same quatity of files into persistent memory,
let alone the user may have to buy multiple NVDIMMs that eats up the precious
DIMM slots that could have been used to insert DRAMs.  
