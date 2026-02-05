# Observation

- `ls` executes in user space.
- To list directory contents, it requests access to filesystem data.
- Those requests cross into the kernel via system calls (e.g., `openat()`, `getdents64()`, `close()`).
- This confirms the kernel is responsible for privileged operations like filesystem access,
  while user-space programs request those operations through a controlled interface.
- Using strace, it important for debugging and how Linux commands interact with the kernel by observing the system calls they use to
  access files, memory, and other system resources.