# soskernel
Security patch for linux kernel allowing to define sys calls and capabilities at process filename level. It was quite interesting project related to linux security, applicable to kernel 2.6.28-7. Stays here just for showing off and next generations which would be interested in kernel patching and security at system calls level.

## Usage

Kernel patch consists of two features. Limiting the system calls and capabilities. For system calls the patched kernel search for `/proc/sos/syscalls/<syscall_name>` where syscall_name must be one of the supported call names avaiable within system. One can set also the return value that should be returned when access to call is denied. For capabilities kernel reads `/proc/sos/capabilities` where every capability represents one bit of 14-bit string. 

## How it is patched

Just seven system calls are patched to show the simplicity. The routing `sos_is_syscall_allowed` makes all the magic inside `sos.c`.

```C
if (!(sos_is_syscall_allowed(__NR_dup2, current, &fake_return_value, 1)))
  return fake_return_value;
```
For capability it's very similar:

```C
if (sos_is_capable(current, has_capability(current, cap), cap))
```


