# soskernel
Security patch for linux kernel allowing to define sys calls and capabilities at process filename level. It was quite interesting project related to linux security, applicable to kernel 2.6.28-7. Stays here just for showing off and next generations which would be interested in kernel patching and security at system calls level.

## Usage

Kernel patch consists of two features. Limiting the system calls and capabilities. For system calls the patched kernel search for `/proc/sos/syscalls/<syscall_name>` where syscall_name must be one of the supported call names avaiable within system. For capabilities kernel reads `/proc/sos/capabilities` where every capability represents one bit of 14-bit string.


