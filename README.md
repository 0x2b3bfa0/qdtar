# qdtar

A `qdtar` archive is a slightly modified `tar` archive, used to pack the root filesystem in the Qisda ES600 e-reader upgrades. The file name used for these archives is `rootfs.img`, even if it has nothing to do with a disk image.

***

The file format is simple: a header of 978 bytes whose contents are completely ignored, prepended to a normal `tar` archive. 

The [executable found on the firmware](busybox) zero-fills the header when creating a new archive. However, the archives found in official firmware upgrade packages used a different approach:

* The first 970 bytes of the header were filled with a copy of the first 970 bytes of the `tar` file.
* The next 8 bytes were used to store the magic number (`QDTAR1.0`).

I suspect that the filling of the header with a copy of the first bytes of the `tar` file is a mistake made by the developer of the packer app. Probably the original code shifts the data on a buffer by copying it to the new offset without taking care of zeroing the contents of the header. The other possibility (more conspiranoid) is that copying the first bytes of the `tar` archive will fool a normal decompression utility.

