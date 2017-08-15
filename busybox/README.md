# Original `qdtar` BusyBox applet

Here is the original binary found on one of the many Qisda ES600 firmwares.

That executable is a trimmed-down copy of BusyBox 1.7.2 that only includes the following applets:

  * `tar`
  * `gzip`
  * `uncompress`

While the former one was wisely renamed to `qdtar` and slightly modified to skip the custom header, the latter ones seem to remain untouched.

I didn't bother to make a full static reverse engineering of the binary, as considering it a black box was enough for documentation purposes.

I'll request the source code of this binary, because BusyBox is licensed as GPLv2, and any derived work from it must follow the same license.

***

Sample output of running `qdtar` renamed as `busybox`:

    BusyBox v1.7.2 (2010-10-27 14:58:03 CST) multi-call binary
    Copyright (C) 1998-2006  Erik Andersen, Rob Landley, and others.
    Licensed under GPLv2.  See source distribution for full notice.
    
    Usage: busybox [function] [arguments]...
       or: [function] [arguments]...
    
            BusyBox is a multi-call binary that combines many common Unix   utilities into a single executable.  Most people will create a
            link to busybox for each function they wish to use and BusyBox
            will act like whatever it was invoked as!
    
    Currently defined functions:
            gzip, qdtar, uncompress
