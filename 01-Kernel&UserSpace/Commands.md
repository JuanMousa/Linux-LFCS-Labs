# Commands Used

```bash
# Run ls and observe system calls in real time
strace ls

# Save the system call trace to a file (stderr redirected)
strace ls 2> ls_syscalls.txt
