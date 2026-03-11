# 01 – Kernel & User Space

## Purpose
The goal of this lab is to understand the separation between user space and
kernel space and how user programs interact with the Linux kernel.

## What I focused on
- Where user-space programs run
- Why they cannot access disk, memory, or hardware directly
- How the kernel is involved even in simple commands like `ls`

## What I did
I used the `strace` tool to observe how the `ls` command behaves at runtime.

By tracing `ls`, I could see that the command itself runs in user space and
requests filesystem access through system calls such as `openat()` and
`getdents64()`. The kernel performs the actual privileged operations and
returns the results to the program.

## What I learned
This lab clearly shows the responsibility split:
- User-space programs request operations
- The kernel validates and executes those operations

This separation is a core security and stability principle in Linux.

## Additional learning: stdout, stderr, and redirection
While working with `strace`, I also practiced Linux output redirection.

Linux programs use standard streams:
- stdin (0)
- stdout (1)
- stderr (2)

`strace` writes its tracing output to stderr, so redirecting stderr is required
to save the trace to a file:

```bash
strace ls 2> ls_syscalls.txt
