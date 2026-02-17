# Observations – System Calls and File Access

## 1. Tracing cat /etc/passwd

When running `cat /etc/passwd`, the program executed in user space.
To read the file, it issued system calls to the kernel.

The important system calls observed were:

- openat() → request to open the file
- read() → request to read file data
- write() → output to terminal
- close() → release the file descriptor

This confirms that user space programs cannot directly access files.
All file operations are handled by the Linux kernel.

## 2. Tracing cat /etc/shadow

When attempting to read `/etc/shadow`, the system call:

openat() returned: EACCES (Permission denied)

This shows that the kernel checks file permissions and denies unauthorized access.

## Conclusion

All file I/O operations occur through system calls.
The Linux kernel enforces security and controls access to system resources.
User space programs cannot bypass these checks.
