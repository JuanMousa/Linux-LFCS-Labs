# Linux System Calls Lab – File Access Control

## Objective
Understand how user space programs interact with the Linux kernel to access files.

## Tools Used
- strace
- cat
- Linux file permissions

## Experiment

1. Traced system calls of:
   cat /etc/passwd

2. Attempted unauthorized access:
   cat /etc/shadow

## Key Findings

- File access occurs through system calls like openat(), read(), write(), and close().
- The kernel validates permissions before allowing access.
- Unauthorized access results in EACCES (Permission denied).

## Learning Outcome

This lab demonstrates:
- Kernel vs User Space separation
- System call mechanism
- Linux security enforcement
- Practical use of strace for debugging
- git commands "git commit -o. --only"